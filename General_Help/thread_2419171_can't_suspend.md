---
title: "can't suspend"
date: 2019-05-17
forum: General Help
---

### Post by cmcanulty on 2019-05-17
I have tried numerous searches and fixes but nothing works. I have an HP Omni200 all-in-one computer. I can't suspend. It is annoying because every fix I try, when it doesn't work requires a restart. After clicking suspend and then resuming  the hard drive spins up and screen goes white or blue but I can't get to a graphical desktop. Keyboard shortcuts, various power manager fixes don't work. I am running xubuntu 18.04.

I got this answer on an xfce forum and tried to implement the solution.

" on the internet on Omni200 says that adding "pci=nomsi" to the kernel boot options fixes suspend.
[https://askubuntu.com/questions/1104219](https://askubuntu.com/questions/1104219) … nomsi-mean"

So I edited and updated grub and it made no difference. Here is my new grub file.  One difference is after the grub change it takes much longer to boot. Did I make a mistake or does anyone have another solution?

```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=nomsi"
GRUB_CMDLINE_LINUX="nouveau.modeset=0"
```

---

### Post by dino99 on 2019-05-17
how the bios set about powersaving ?

---

