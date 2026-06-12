---
title: "cryptsetup LUKS passphrase for usb flash drive only works on one system?"
date: 2007-02-19
forum: General Help
---

### Post by 944jon on 2007-02-19
I used this how-to to encrypt my 256Mb USB flash drive with cryptsetup and LUKS formatting. 

[http://www.emcken.dk/weblog/archives/164-Encrypted-USB-drive-in-Ubuntu.html]("http://www.emcken.dk/weblog/archives/164-Encrypted-USB-drive-in-Ubuntu.html")

It works fine on my desktop and prompts for the passphrase automatically when I insert it, but when I try to open it on my laptop it says the passphrase is wrong? both systems are running ubuntu 6.10 and have cryptsetup package installed. There are 2 partitions on the drive:
/dev/sda1 mounted to /media/usbdisk is a 16Mb encrypted LUKS fat32 filesystem
/dev/sda2 mounted to /media/usbdisk-1 is an unencrypted ext2 filesystem and mounts automatically on either system.

Can I use a passphrase or do I need to use a key in order to be portable to multiple systems? 
Does this have anything to do with different UUID between systems (username is the same) or ownership issues? Is there a way to always have it mounted as root ownership?

---

### Post by mat_london on 2007-02-20
Me too,

USB on old laptop packed up so I can't plug my encrypted backup disc into it.
The LUKS password doesn't work on my new laptop.

Guessing there must be a second key somewhere on the system ??

HELP !


Mat

---

### Post by mat_london on 2007-02-20
Try 

sudo modprobe dm-crypt

worked for me

Mat

---

