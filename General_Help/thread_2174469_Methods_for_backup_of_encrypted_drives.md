---
title: "Methods for backup of encrypted drives?"
date: 2013-09-14
forum: General Help
---

### Post by PaulBx on 2013-09-14
I have whole disk (except /boot of course) encryption, and have been using dd to copy the entire disk image to a usb drive (after having booted Puppy Linux off a flash drive so no hard drive files will be open during the backup). This has the advantage of keeping my save set encrypted also.  The disadvantage, of course, is that it takes a long time. Another disadvantage is that my new computer uses UEFI boot so booting off a flash drive is more tedious than it used to be, requiring me to go in and fool with the bios first.  I was looking at rsync, to reduce the amount transferred and also to be able to increase its frequency (e.g. overnight), but I don't want my save set in clear text.  Maybe my solution is just to buy a USB v3 drive and stick with the old way of doing it? Any thoughts or recommendations?  I will continue digging around for answers; I can't be the first user with this problem...

---

### Post by sudodus on 2013-09-14
The backup will be easier to manage in clear text, and if you keep it in a safe place, it should be OK.

But the idea of having the backup encrypted can be attractive. I think that if you boot from a modern Ubuntu 64-bit CD/DVD/USB drive (12.04.2 or newer), it can comply with the BIOS/UEFI settings and should be able to work without tampering with the BIOS menu settings. (Your Puppy is probably 32-bit, and cannot run with UEFI.) 

USB 3 is really much faster than USB 2. eSATA is also a fast alternative when available. For desktops there are simple and cheap eSATA 'cards', actually only the plate and the connector converting from SATA (internal) to eSATA (external). And laptops might have either of them, USB 3 or eSATA. Many new laptops have a USB 3 port.

But the compression (when you make a compressed image file) might be the bottleneck, that limits the speed.

---

### Post by PaulBx on 2013-09-14
Thanks for responding. Yes, Puppy is 32 bit, so that may explain some of the problems. I think there is a 64-bit Puppy called "Fat Dog".  I may try an Ubuntu boot device to see where that gets me. Another thing that occurs to me is to simply do a dual-boot arrangement on my hard drive with some stripped down OS that will just be used for backing up the "real" partition and nothing else. Then I won't care about open files for that side of things. But then I'd have to shorten my current partition which may be a pain, seeing as it is encrypted and "lvm'd". Don't know if gparted is smart enough to handle that.  My computer has a couple USB v3 ports.  Normally I compress my cleartext backups (of other machines), and generally fill the unused space with zeros first so the compression is efficient. But I suspect compressing encrypted data is not going to result in much of a squeeze. So I just may skip compression altogether. My disk, being an SSD is not huge so I won't overwhelm my backup drive.  I am getting the impression you are suggesting there are no backup tools to generate an encrypted save set. So I should just stick with dd.  That's OK I suppose.

---

### Post by sudodus on 2013-09-15
Yes, I think you can stick with dd. But switch to using an Ubuntu 64-bit CD/DVD/USB drive (12.04.2 or newer), that can comply with the  BIOS/UEFI settings and should be able to work without tampering with the  BIOS menu settings! If you think Ubuntu is slow, get a Lubuntu 64-bit CD/DVD/USB drive (12.04.2 or newer), which boots faster. (I don't know if Puppy manages UEFI.)

You can try different block sizes for dd. I have found that bs=4096 (instead of default 512 bytes) is optimal or near-optimal in many computers.

You can test compression. If you let dd make an image file, it is easy to compress that file with gzip afterwards and to find out if it is worthwhile.

```
 cd target-directory
```
```
 sudo dd if=/dev/sda of=dd-backup.img bs=4096
```
```
 gzip -c dd-backup.img > dd-backup.img.gz
```

---

