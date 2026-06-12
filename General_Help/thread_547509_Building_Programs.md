---
title: "Building Programs"
date: 2007-09-10
forum: General Help
---

### Post by GlacierBill on 2007-09-10
A few times I have tried to build programs, I just tried to build bidwatcher and get an error. I use the command sudo ./configure and get this error "checking for C compiler default output file name... configure: error: C compiler cannot create executables",  Any ideas?

---

### Post by Tomosaur on 2007-09-10
You need to install the build-essential package:
```

sudo apt-get install build-essential

```

Good luck!

---

