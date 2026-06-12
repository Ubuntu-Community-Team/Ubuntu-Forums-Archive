---
title: "Why wont Steam work with Quantal Quetzal 12.10?"
date: 2013-01-27
forum: General Help
---

### Post by smitty4478 on 2013-01-27
I have Quantal Quetzal 12.10 64-bit and Steam wont install on it, I have the latest steam downloaded from the site but when I try to install it, the Ubuntu Software Center says "Wrong Architecture 'i386'." So what do I do? If I'm not mistaken it's because they don't have it ready for 12.10 yet but I'm not sure that's why I'm asking you guys, so thanks! :)

---

### Post by mcduck on 2013-01-27
They do have a version for 12.10, and it works just fine. The problem here is that they only have a 32-bit version, and I assume you are running a 64-bit Ubuntu. Hence the error about wrong architecture.

Easy thing to solve, though, just install the [ia32-libs]("apt:ia32-libs") package.

---

### Post by swarfega on 2013-01-27
I am using Kubuntu 12.10 64-bit and can confirm Steam works fine. Whether its a difference between Ubuntu and Kubuntu I don't know.

---

### Post by smitty4478 on 2013-01-28
> **mcduck said:**
> They do have a version for 12.10, and it works just fine. The problem here is that they only have a 32-bit version, and I assume you are running a 64-bit Ubuntu. Hence the error about wrong architecture.

Easy thing to solve, though, just install the [ia32-libs]("apt:ia32-libs") package.

I tried installing it and it said that it couldn't be installed because it was missing other components.

---

