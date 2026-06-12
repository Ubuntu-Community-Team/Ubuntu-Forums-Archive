---
title: "Help!  Ubuntu won't start"
date: 2008-06-06
forum: General Help
---

### Post by jonathanpeter on 2008-06-06
I've been using Ubuntu 8:04 without issues.  Yesterday, I installed the latest updates, rebooted - everything worked fine.  

Today, I loaded Ubuntu, and it won't boot.  I get as far as the text which says something like

"Loading..." - (just before the grub boot option screen) - a split second after seeing this text, the the computer reboots.  And the cycle repeats again and again.

I've booted on the live CD and tried to reinstall grub with:

grub-install /dev/sda

But I get the following error

/dev/sda does not have any corresponding BIOS drive.

I can confirm that /dev/sda is the correct device.  I can mount it and see all my linux files.

How can I resolve this error?

Lost of thanks in advance.

---

### Post by kpkeerthi on 2008-06-06
An easy way to fix your GRUB is by using Super GRUB disk.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

### Post by rraj.be on 2008-06-06
Read this first.

You may get more ideas with easy to track problems and solutions


```
[http://www.gentoo.org/doc/en/grub-error-guide.xml]("http://www.gentoo.org/doc/en/grub-error-guide.xml")
```

---

### Post by jonathanpeter on 2008-06-06
Thanks very much for your help.  It worked

---

