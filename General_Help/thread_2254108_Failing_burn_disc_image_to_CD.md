---
title: "Failing burn disc image to CD?"
date: 2014-11-25
forum: General Help
---

### Post by flaymond on 2014-11-25
Hey, I try to install minimal installer now....but I failed to burn .iso using brasero to a disk (Blank CD-RW). It say burn is success...and auto ejected...but when I mount it back...the cd still blank....how can I fix this? I only got a USB (using it right now as Live USB of Linux Mint 7.1 and cannot boot anything unless using this USB) and the blank CD-RW. How can I fix this? Please help. I tried to change the properties of the speed burning to 4.0...but still failed....:(

---

### Post by sudodus on 2014-11-25
I use ***k3b***, which is a reliable and fairly easy to use tool for burning. It is straight-forward to burn an image from an isofile. You are already aware of the advantage of burning slowly.

-o-

The mini.iso is so small, that you might not see the burned track :-) Did you try booting from it?

Did you check with md5sum that the download was good?

Are you sure that the computer tries to boot from the CD/DVD drive?

If your computer is running in ***UEFI*** mode, you need to boot from an Ubuntu flavour ***desktop*** iso file. The mini.iso and the alternate iso files of Lubuntu only work in BIOS (alias CSM) mode.

If still no go, maybe the disk is bad. CD and DVD disks are mass-produced, and some of them are bad from the factory. Try with another disk!

---

### Post by flaymond on 2014-11-25
Thanks for the advice

---

