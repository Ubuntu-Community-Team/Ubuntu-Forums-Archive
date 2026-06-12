---
title: "Installing Tar Archives"
date: 2007-06-02
forum: General Help
---

### Post by gspott99 on 2007-06-02
I have recently installed Feisty Fawn after getting thoroughly annoyed with Vista on my laptop.  I am trying to install VMware so I can run an LIS, but after unpacking the tarball I cannot compile it...apparenly the C Compiler is either missing or not operational.

Are there any good C Compilers out there that I can get off the repositories or more to the point how can I make sure the compiler I have is working?

(I've tried unpacking a few tarballs since I've installed and all of them fail because of the C Compiler).

Thanks

---

### Post by taurus on 2007-06-02
Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

