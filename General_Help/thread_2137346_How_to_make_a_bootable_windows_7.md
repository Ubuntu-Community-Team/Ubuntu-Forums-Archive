---
title: "How to make a bootable windows 7?"
date: 2013-04-20
forum: General Help
---

### Post by Sethun on 2013-04-20
Well I need to reinstall windows, I don't have big enough discs and I have a USB flash drive, except Unetbootin doesn't have the "show all drives" option anymore. And start-up disc creator is mainly for ubuntu, I'm really stumped here. Anybody got any alternatives or any work arounds?

---

### Post by Mark Phelps on 2013-04-20
We would first need to know what you HAVE in order to make a disk from that you could then use to reinstall Windows.  You will have to make the disk from something.

---

### Post by Sethun on 2013-04-20
> **Mark Phelps said:**
> We would first need to know what you HAVE in order to make a disk from that you could then use to reinstall Windows.  You will have to make the disk from something.

I have a usb flash drive I want to put all the contents of the ISO file in and mark the boot flag in gparted. Expect when I mount the iso file it's always empty, bt command ls shows that there are files there I just can't get them to show up.

---

### Post by Cheesemill on 2013-04-20
You could try using WinUSB.

[http://www.webupd8.org/2012/01/tool-to-create-windows-usb-install.html](http://www.webupd8.org/2012/01/tool-to-create-windows-usb-install.html)

---

### Post by C.S.Cameron on 2013-04-20
Using the Ubuntu Live CD/DVD/USB

Use gparted to format the USB as NTFS and set boot flag.
Extract the Win 7 ISO to the USB using Archive Manager.
That's it, boot and install

(Extract the ISO, not copy, you want files and folders)
Alternately you could copy the Win 7 DVD to the USB.

---

### Post by Mark Phelps on 2013-04-21
Notice that C.S.Cameron said "Extract ...".  That's very important -- as copying the ISO file to the USB stick will not accomplish what you want.

---

