---
title: "apps list command"
date: 2007-04-20
forum: General Help
---

### Post by tubunu on 2007-04-20
What's the command line for listing all installed applications on the system? Thanks.

---

### Post by fanatik on 2007-04-20
$ dpkg -l

:)

---

### Post by tubunu on 2007-04-22
Any way to stop the list halfway? There are so many packages listed, I can only see **l**ibgpod1 through **z**oo. I'd like to see them starting with the letter **A**.

---

### Post by Swab on 2007-04-22
> **tubunu said:**
> Any way to stop the list halfway? There are so many packages listed, I can only see **l**ibgpod1 through **z**oo. I'd like to see them starting with the letter **A**.

dpkg -l | less

---

