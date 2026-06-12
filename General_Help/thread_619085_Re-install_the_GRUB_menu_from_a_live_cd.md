---
title: "Re-install the GRUB menu from a live cd"
date: 2007-11-21
forum: General Help
---

### Post by Shinbu-Otaku on 2007-11-21
Hello,

My problem is that my GRUB boot menu has dissapeared. I had 64 Studio, Ubuntu 7.10 and Windows XP on my pc. Last nite i formatted the hard drive with 64 Studio on (as i no longer use it) and now when i reboot my pc it says

Grub Loading, Please Wait...
Error 22

and does not go any further. Is there a way of me re-installing the grub menu, or editing it to pick up ubuntu and windows again, from the Ubuntu live cd? I have quite a few files on my ubuntu partition that i need, so im hoping not to have to format it.

Thanks

---

### Post by asgard_command on 2007-11-21
Ive had to do this several times. 

I think its just sudo grub-install /dev/sda  (or hda) to intstall it back to the mbr

I remember at one time having to run 
sudo grub
find /boot/grub/stage1

root (hd?,?)

setup (hd0)

But I am just going from memory and from what I was told at the time.

---

### Post by edwardTheGreat on 2007-11-21
[http://users.bigpond.net.au/hermanzone/p15.htm]("http://users.bigpond.net.au/hermanzone/p15.htm")

is a great spot for info about GRUB and how to do things GRUB related.

---

### Post by zvacet on 2007-11-21
[http://ubuntuforums.org/showthread.php?t=224351&highlight=grub]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub")

---

### Post by Shinbu-Otaku on 2007-11-21
Thanks everyone, hopefully this will solve my problem :)

---

### Post by ronmarley1 on 2007-11-21
Another great tool that has helped me quite a few times is the SuperGrubDisk.  It even has tools to repair the Windows bootloader.  Here's one of many links to download: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

