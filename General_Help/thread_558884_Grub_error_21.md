---
title: "Grub error 21"
date: 2007-09-24
forum: General Help
---

### Post by Obeleh on 2007-09-24
Hi.

Today I have bought a 500GB external HD. I figured now I could install linux on my laptop. My laptop is a Dell latitude D610. And had winxp installed. This laptop is from the company I work for. That is why I keep XP on it and I dont want to install linux on the internal HD. So I managed to install Ubuntu on the external HD (working fine). But now when I want to boot my laptop without my USB HD grub throws an error at me: Error 21. Wich apparently means it cant find the hard disk. Thats normal. But I dont always have my USB HD with me.

Is there a way to let the laptop boot to XP straigt away w/o USB HD. And boot to grub (or straight to ubuntu) when its plugged in?

---

### Post by rsambuca on 2007-09-24
You will need to create a small /boot partition on your internal drive where you can load the grub loader to.  Then, when you boot up you will have the choice of selecting Windows or Ubuntu.

---

### Post by Obeleh on 2007-09-24
that sound good.

How do I do this? I dont want to loose anything from my Cdrive. For my D-drive I can make a backup

---

### Post by rsambuca on 2007-09-24
You will have to create a new partition on the C: drive in order for this to work.  You can do this using gParted which is on the Ubuntu LiveCD, or you can download and use the [gParted LiveCD]("http://gparted.sourceforge.net/").  There is a small chance of data loss, so make sure you back up sensitive data on the drive first.

---

### Post by ajgreeny on 2007-09-24
I assume you let ubuntu put grub on the default drive, ie your internal windows hard disk.  If so an even better way to overcome your problem is to restore the windows mbr and then install grub on the external drive and set that to be the first boot device, with the internal hard disk as second boot device.

Now when you boot with the external drive attached you will get the grub menu and can chose either ubuntu or windows.  If the external drive is not attached the system will automatically boot from the second boot device, the internal hard disk, as it will not find the external drive and therefore grub will not appear.  A rather elegant way round the problem, I think.

---

### Post by psusi on 2007-09-24
You can do that by using the FIXMBR command from the windows recovery console to remove the grub MBR from the internal disk, then installing grub on the external disk like this:

sudo grub
device (hd0) /dev/sdb
root (hd0,1)
setup (hd0)

This assumes of course, that the external disk shows up as /dev/sdb, and your / ( or /boot if you have a separate partition for it ) is on the first partition on that disk.

---

### Post by rsambuca on 2007-09-24
> **ajgreeny said:**
> I assume you let ubuntu put grub on the default drive, ie your internal windows hard disk.  If so an even better way to overcome your problem is to restore the windows mbr and then install grub on the external drive and set that to be the first boot device, with the internal hard disk as second boot device.

Now when you boot with the external drive attached you will get the grub menu and can chose either ubuntu or windows.  If the external drive is not attached the system will automatically boot from the second boot device, the internal hard disk, as it will not find the external drive and therefore grub will not appear.  A rather elegant way round the problem, I think.

Ahh...  it is indeed!  I keep forgetting about this method because my rig won't boot from usb drives.

---

