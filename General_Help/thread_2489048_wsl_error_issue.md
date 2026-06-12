---
title: "wsl error issue"
date: 2023-07-17
forum: General Help
---

### Post by will1010 on 2023-07-17
WSL (8) ERROR: CreateProcessEntryCommon:370: getpwuid(0) failed 2
trying to boot up my wsl and it keeps shutting down, displays the above error, anyone know what the issue could be?

---

### Post by yancek on 2023-07-17
Have you tried the suggested solution at the page at the link below?

[https://github.com/microsoft/WSL/issues/5923](https://github.com/microsoft/WSL/issues/5923)

---

### Post by MAFoElffen on 2023-07-17
In a Windows Command Prompt, what is the output of
```

wsl -l

```
Please post the output within Code Tags.

---

