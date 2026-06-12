---
title: "zip with password"
date: 2022-10-06
forum: General Help
---

### Post by Old Jimma on 2022-10-06
hello forum people:

I want to automate zipping files with a password from the command line.

I've tried

> 
zip -P secretpassword -er folder1 folder1.zip


This procedure then goes interactive and asks me for a password.

How do I write that code so that it doesn't go interactive?

Thanks,
Old

---

### Post by merilyn2 on 2022-10-06
This command works in my case in Ubuntu 22.04:

```
zip -P secretpassword -r folder.zip folder
```

---

### Post by Old Jimma on 2022-10-07
Why did you not include the "e" option to encrypt?

---

