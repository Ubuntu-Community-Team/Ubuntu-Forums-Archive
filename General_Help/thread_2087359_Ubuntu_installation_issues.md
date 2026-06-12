---
title: "Ubuntu installation issues"
date: 2012-11-23
forum: General Help
---

### Post by Hiuhu on 2012-11-23
I am using a lenovo G580 to install ubuntu 12.04 and every time it starts installing this error is shown :

The 'grub-efi' package failed to install into /target/. Without the GRUB boot loader, the installed system will not boot.
I have even tried these commands:
sudo grub-install /dev/sda
sudo update-grub
but none seem to work hence the installation does not complete anyone with any idea please help

---

### Post by NikTh on 2012-11-23
Hi , 
what architecture of Ubuntu trying to install ? 32bit or 64bit ? If the answer is 32bit then...
... Grab the 64bit-PC architecture and try again:  [http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)
Thanks

---

### Post by Hiuhu on 2012-11-23
Am using the 64bit architecture.

---

### Post by Isamu715 on 2012-11-23
I think [NikTh]("http://ubuntuforums.org/member.php?u=1566509") meant the architecture of the install disk. If you downloaded the 32-bit ISO try 64-bit instead.

---

