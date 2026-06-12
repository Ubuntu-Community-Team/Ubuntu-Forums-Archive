---
title: "Need to secure erase a Samsung SSD but it's locked &amp; won't let me?"
date: 2015-12-30
forum: General Help
---

### Post by PsychedelicWonders on 2015-12-30
I put Ubuntu 14.04 on an Samsung SSD 850 and encrypted it via Ubuntu with a password, which I do know, but my grub menu is messed up from also installing windows and now I can't get the ubuntu SSD to load and want to just secure erase the SSD because it's locked because of the Ubuntu encryption password.

Any advice on what my options are on how to get around this?

I'd prefer to just secure erase it so I can use it on a new build.

---

### Post by sudodus on 2015-12-30
I think you need not secure erase an encrypted drive. It is enough to 'forget' the password and the data will be securely erased.

It should be enough to wipe the first megabyte and make a new partition table. You can do that easily via [mkusb's wipe menu](https://help.ubuntu.com/community/mkusb/wipe).

If you want to wipe the whole drive anyway, there are better tools than mkusb for 'full size drives', HDDs and SSDs, while mkusb is good for pendrives. You can use DBAN or hdparm, but in your case I think it would only cause unnecessary wear of the flash memory hardware.

---

### Post by leunam12 on 2015-12-30
Have you tried the disk erasing tool in partedMagic? Check the tutorial below, that's what I have done in the past.

[http://www.cnet.com/how-to/how-to-securely-erase-an-ssd-drive/](http://www.cnet.com/how-to/how-to-securely-erase-an-ssd-drive/)

---

### Post by PsychedelicWonders on 2016-01-12
> **sudodus said:**
> I think you need not secure erase an encrypted drive. It is enough to 'forget' the password and the data will be securely erased.

It should be enough to wipe the first megabyte and make a new partition table. You can do that easily via [mkusb's wipe menu]("https://help.ubuntu.com/community/mkusb/wipe").

If you want to wipe the whole drive anyway, there are better tools than mkusb for 'full size drives', HDDs and SSDs, while mkusb is good for pendrives. You can use DBAN or hdparm, but in your case I think it would only cause unnecessary wear of the flash memory hardware.

I'm trying to use Samsung's Secure Erase to bring the SSD back to factory new, but it is COMPLETELY locked out because of the encryption, it won't touch it through Secure Erase or through Samsung's Magic program - it's totally locked out.

Windows is also completely screwed on my computer as well, so I'm looking at a giant paper weight of a computer system at the moment.

I THINK if I can set GRUB to boot from the Ubuntu SSD, I can get it and fix it since I do know the encryption password - but how do I change the grub menu if I can't get windows or Ubuntu to load off their SSDs?

> **leunam12 said:**
> Have you tried the disk erasing tool in partedMagic? Check the tutorial below, that's what I have done in the past.

[http://www.cnet.com/how-to/how-to-securely-erase-an-ssd-drive/](http://www.cnet.com/how-to/how-to-securely-erase-an-ssd-drive/)

I haven't tried yet, this is my only computer at the moment I have access to, I'm on a chromebook right now and you can't do jack on these things besides browse the web.

If I can get grub to load the Ubuntu SSD I can possible fix this whole problem.  

If I can't I will see if there is a friends computer I can use to load up a USB drive.

Would I be better to do partedmagic or Ubuntu Live instead?

Basically this is a complete mess and now my windows SSD is so jacked up it won't even load/install windows anymore.  Windows has crashed probably 10 times these last couple months during their updates.

---

### Post by sudodus on 2016-01-12
I think it is a good idea to make a DVD boot disk or USB boot drive with Ubuntu or maybe some linux rescue operating system.

Boot live from the DVD/USB drive with the SSD connected and check if the SSD is recognized as a mass storage device. Please post the output of the following commands

```
df

sudo parted -ls

sudo lsblk -fm
```

There is hope if the drive is recognized as a mass storage device /dev/sdx, where x is the drive letter. Then you should be able to use ***mkusb*** to wipe the first megabyte and after that create a new partition table and file system with several tools, for example ***gparted*** or the Ubuntu installer (ubiquity).

Otherwise you should check the SSD in another computer and try to find out if the SSD or your computer is damaged.

---

