### gopherjs
---
https://github.com/gopherjs/gopherjs

```go
// tests/gorepo_test.go

func TestGoRepositoryCompilerTests(t *testing.T) {
  if runtime.GOARCH == "js" {
    t.Skip("test meant to be run using normal Go compiler (needs os/exec)")
  }
  
  args := []string{"go", "run", "run.go", "--summary"}
  if testing.Verbose() {
    args = append(args, "-v")
  }
  cmd := exec.Command(args[0], args[1:]...)
  cmd.Stdout = os.Stdout
  err := cmd.Run()
  if err != nil {
    t.Fatal(err)
  }
}

func TestGopherJSCanBeVendored(t *testing.T) {
  if runtime.GOARCH == "js" {
    t.Skip("test meant to be run using normal Go compiler (needs os/exec)")
  }
  
  cmd := exec.Command("sh", "gopherjsvendored_test.sh")
  cmd.Stderr = os.Stdout
  got, err := cmd.Output()
  if err != nil {
    t.Fatal(err)
  }
  if want := "hello using js pkg\n"; string(got) != want {
    t.Errorf("unexpected stdout from gopherjsvendored_tes.sh:\ngot:\n%s\nwant:\n%s", got, want)
  }
}


```

```
```

```
```


