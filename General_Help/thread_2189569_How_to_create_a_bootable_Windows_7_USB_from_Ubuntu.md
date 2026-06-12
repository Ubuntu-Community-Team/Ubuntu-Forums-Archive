---
title: "How to create a bootable Windows 7 USB from Ubuntu?"
date: 2013-11-23
forum: General Help
---

### Post by renato3 on 2013-11-23
Hi, I'm currently using Ubuntu 13.10 and I need to install Windows 7 in dual boot. I already have the ISO image. Which program could I use to create a bootable Windows 7 USB disk using this ISO image I have?

---

### Post by fantab on 2013-11-23
You can do it with Unetbootin.

To install Unetbootin:
```
sudo apt-get install unetbootin
```

For more Info: [http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by renato3 on 2013-11-23
I already have unetbootin installed. Does it work with Windows ISO too? I thought it worked only with Linux ISOs.

---

### Post by renato3 on 2013-11-23
Is there a way of creating a Windows 7 bootable USB using gparted?

---

### Post by sgage on 2013-11-23
> **renato3 said:**
> I already have unetbootin installed. Does it work with Windows ISO too? I thought it worked only with Linux ISOs.

I am pretty sure I successfully used unetbootin to make a Windows 7 USB stick from the iso file - I remember being somewhat surprised that it worked.

---

### Post by renato3 on 2013-11-25
In the end I needed to borrow a notebook with Windows to use Rufus to create a bootable UEFI Windows 7 pen drive :(

---

