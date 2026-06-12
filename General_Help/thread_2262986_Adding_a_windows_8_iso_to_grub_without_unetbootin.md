---
title: "Adding a windows 8 iso to grub without unetbootin"
date: 2015-01-28
forum: General Help
---

### Post by kade2 on 2015-01-28
I wanted to add windows 8 to my GRUB 2 because I need windows alongside ubuntu.
I've looked all day and found nothing that looks safe to do. I tried unetbootin but it just gets frozen when I try to select to boot into "unetbootin" in grub
So now I'm trying to find a menuentry for this iso to add to grub. Is there an easier way?
I don't have a big enough flash drive to make a booting drive nor do I have a cd anymore. I do have a recent iso of windows 8.1 install located in /windows.iso

---

### Post by yancek on 2015-01-28
Unetbootin is software to create bootable flash drives of LINUX systems and won't work with windows proprietary software.
Grub2 won't directly boot the proprietary windows iso either.
You can put the windows 8 extracted iso file either on a partition on a flash drive or on your hard drive and boot it from Grub2 to install.  The link below explains it and it does work.

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

I would recommend reading all the way through it several times before trying it if you are not familiar with Grub2.

---

