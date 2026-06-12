---
title: "How to : go back to a older kernel"
date: 2007-06-04
forum: General Help
---

### Post by frenchy82 on 2007-06-04
Hello,

We had an update of the kernel from 2.6.20.15 to 2.6.20.16

Every thing was ok for wubi (and thanks for it)

But this kernel is not very stable on my laptop so i wanted to go back to the 20.15

So i changed the name of the initrd.gz.old and linux.old and it works great.

But today after a re boot of my laptop it go back to the 20.16 alone?

Is there a way not to use the 20.16 version. (i'm waiting for the 20.17, hoping it will be better)

Thanks a lot

I hope you could understand what i want to say in my "english :( )

---

### Post by ago on 2007-06-04
change the default settings in /boot/grub/menu.lst. To be able to choose the kernel at boot remove the "hidemenu" line and increase timeout.

---

### Post by esavato on 2007-06-04
ditto to the last post.  edit the grub menu.lst, comment out the timeout (# in front) and the next time you boot, you can choose the older kernel.

---

### Post by frenchy82 on 2007-06-04
Many thankks  both :p

---

### Post by frenchy82 on 2007-06-04
Oh, sorry i didn't succeed with it
My version of wubi is
version=7.04-v1

I dont have folder grub in the ubuntu boot folder

In the win partition i have c:\\wubi\boot\menu.lst
if i make the changes on it, on the boot i have only "UBUNTU" in the choice to boot and it boot on the last kernel

thanks

---

### Post by ago on 2007-06-04
download the new version of wubi from the website then [www.wubi-installer.org](www.wubi-installer.org)

---

### Post by frenchy82 on 2007-06-04
Thanks for the answer,

If i install it, i will loose all what i have done on UBUNTU, it's like a new install?

---

### Post by ago on 2007-06-04
> **frenchy82 said:**
> Thanks for the answer,

If i install it, i will loose all what i have done on UBUNTU, it's like a new install?

yes but you can keep the home virtual disk, so all your settings will be kept, we'll do an upgrade package later on. To keep home, copy the file before installing the new wubi then replace c:\wubi\disks\home.virtual.disk with the old file (call it home.virtual.disk)

---

