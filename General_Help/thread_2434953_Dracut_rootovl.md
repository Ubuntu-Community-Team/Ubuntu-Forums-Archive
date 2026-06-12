---
title: "Dracut rootovl ?"
date: 2020-01-14
forum: General Help
---

### Post by Ice-Tea on 2020-01-14
Anyone got Dracut rootovl working with Ubuntu?

Thanks

---

### Post by CelticWarrior on 2020-01-14
You should describe the problem you're having instead of trowing a vague question.

---

### Post by Ice-Tea on 2020-01-14
> **CelticWarrior said:**
> You should describe the problem you're having instead of trowing a vague question.

I can't find a step by step guide for installing Dracut rootovl on either Ubuntu or Debian.

---

### Post by CelticWarrior on 2020-01-14
[https://askubuntu.com/a/262394](https://askubuntu.com/a/262394)

---

### Post by Ice-Tea on 2020-01-14
> **CelticWarrior said:**
> [https://askubuntu.com/a/262394](https://askubuntu.com/a/262394)

I never asked how to install Dracut , where in that guide does it mention rootovl?

---

### Post by bernard010 on 2020-01-18
Dracut Overlay Formatting (ovl) is not mentioned in the man pages.
 [http://man7.org/linux/man-pages/man7/dracut.cmdline.7.html](http://man7.org/linux/man-pages/man7/dracut.cmdline.7.html)

[https://answers.launchpad.net/bugs/1548558](https://answers.launchpad.net/bugs/1548558)
Their is three Bugs for Dracut
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=945596](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=945596)
[URL="https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=409271"]https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=409271

[/URL]Overlayfs : [https://blog.fai-project.org/posts/overlayfs/](https://blog.fai-project.org/posts/overlayfs/)
Be sure to file the bug report and link the other two bugs to it, Please.

---

### Post by bernard010 on 2020-01-18
.ovl file is :  [URL="https://en.wikipedia.org/wiki/OVL"]https://en.wikipedia.org/wiki/OVL
[/URL] The process of transferring a block of program code or other data into main memory,replacing what is already stored.
No it is not working yet.
Dracutis is used to create an initramfs image by copying tools and files from an installed system and
combining it with the dracut framework. Initramfs has one purpose, mounting the root file system so 
the boot process can transition to the real rootfs.
Debian package: Dracut:   [URL="https://packages.debian.org/jessie/dracut"]https://packages.debian.org/jessie/dracut 
[/URL]Packages related to Dracut depends and recommends by Debian.

---

