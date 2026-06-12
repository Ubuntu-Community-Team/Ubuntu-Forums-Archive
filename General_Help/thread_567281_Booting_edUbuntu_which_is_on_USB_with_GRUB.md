---
title: "Booting edUbuntu which is on USB with GRUB"
date: 2007-10-04
forum: General Help
---

### Post by DylanNIRVANA on 2007-10-04
Hi.

I installed edUbuntu to my external hard drive(USB) and i want to add it to my current list of my GRUB setup, only thing is i dont know what to put into the root command since it's on a USB drive
e.g "root (???,?)"

Thanks in advance.

---

### Post by DylanNIRVANA on 2007-10-04
Sorry!
I fixed it:

Fix:-

My BIOS didn't have the 3rd Hard Drive set up, when i set my external hard drive as the 3rd Hard Drive, edUbuntu booted up with root (hd2,0).

---

