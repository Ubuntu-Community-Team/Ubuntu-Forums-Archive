---
title: "High Memory and Default Kernel"
date: 2006-07-17
forum: General Help
---

### Post by Burgresso on 2006-07-17
Quick question, I hope: can you set up the "high memory" option with ubuntu 6.06, default install, without recompiling the kernel? If so, how?

gracias,

burgresso

---

### Post by tseliot on 2006-07-17
> **Burgresso said:**
> Quick question, I hope: can you set up the "high memory" option with ubuntu 6.06, default install, without recompiling the kernel? If so, how?

gracias,

burgresso

Up to 4GB of RAM are enabled if you use a kernel from Ubuntu's repositories ( 686, k7, etc.). And no, there's no need of recompiling the kernel.

---

### Post by Burgresso on 2006-07-17
Awesome, so if you install it it will be enabled automatically? Thank you very much, sir!

---

### Post by tseliot on 2006-07-17
> **Burgresso said:**
> Awesome, so if you install it it will be enabled automatically? Thank you very much, sir!

I'm not 100% sure about linux-386 but if you installed the version which is optimised for your cpu architecture (686, k7, k8, etc.) I'm 100% sure of it.

I have 2GB of RAM and use a k7 kernel. All I did to install it was:
```
sudo apt-get install linux-k7
```

and you'll get also the restricted modules

---

### Post by Burgresso on 2006-07-17
Cool; AMD64 is k7, right?

---

### Post by tseliot on 2006-07-17
> **Burgresso said:**
> Cool; AMD64 is k7, right?

Yes, but only on Ubuntu 32bit. If you install Ubuntu 64bit then you will need a k8 kernel.

---

### Post by az on 2006-07-17
Linux-386 has supported 4 gigs of ram since Breezy.

---

### Post by tseliot on 2006-07-17
> **azz said:**
> Linux-386 has supported 4 gigs of ram since Breezy.

Ok, thanks I wasn't sure. I'm getting old, I suppose :mrgreen:

---

