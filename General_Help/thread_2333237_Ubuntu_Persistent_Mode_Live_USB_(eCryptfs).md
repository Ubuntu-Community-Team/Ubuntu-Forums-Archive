---
title: "Ubuntu Persistent Mode Live USB (eCryptfs)"
date: 2016-08-08
forum: General Help
---

### Post by marioxeron on 2016-08-08
Hello,

I have a USB Flash Disk 16 gigabytes, divided into two partition.

1. partition: Ubuntu 32bit (Live Persistent Mode)
2. partition: "casper-rw"


I am trying to encrypt the folder "/home/" using "eCryptfs"
But I've never done it before Can anyone advise me how?

---

### Post by sudodus on 2016-08-08
Welcome to the Ubuntu Forums :-)

I am not sure that it works with a persistent live drive, to have encrypted home, or in general, to make the system secure.

One solution could be to have a third partiiton encrypted, or a particular directory encrypted, but I dont' think that it is a good secure system.

-o-

Another solution is to install a system (installed like into an internal drive, but into a USB pendrive. But it means that there will be more write operations, which cause wear of the memory cells. You can decrease the wear by using

- the mount option noatime
- the ext2 file system or better the ex4 file system without journaling.

The installed system can be installed with

- either LVM with encrypted disk
- or encrypted home.

Both options are offered by the installer, and I suggest that you use a prepared method rather than a home-made one, because you can easily miss something which causes a security hole.

You must use a password that is hard to guess, and you must remember it. A secure system has no back door ;-)

In general, ***backup is very important for encrypted systems***. Without journaling it will be even more important to take frequent backups.

---

### Post by marioxeron on 2016-08-08
My flash drive is USB 3.0 and laptop has USB 3.0.
(I'm not sure if the boot Ubuntu uses 3.0 or (used USB 2.0 for compatibility)
When I installed Ubuntu on a USB system was very slow.

Installed Ubuntu (Normal HDD or SSD) + encryption use at home (But the work or publicly available computers I want to use Ubuntu Live USB)

My question remains the same...
When using Ubuntu Live in persistent mode (How to encrypt a folder home?)

PS: Excuse my bad English

---

### Post by sudodus on 2016-08-08
I can use USB 3 pendrives successfully both in USB 3 and USB 2 ports of the computer. But the flash hardware is often limiting the read and write speed, so that it is slower than an internal drive. It is important to have a ***fast*** USB 3 drive. See this link and links from it,

[FromUSBStick#Notes_about_speed](https://help.ubuntu.com/community/Installation/FromUSBStick#Notes_about_speed)

If you boot in BIOS mode, it is straight-forward to create a USB 3 boot drive with an installed system. If you avoid proprietary drivers, you can expect it to be portable between the vast majority of PC computers with Intel or AMD processors.

If you boot in UEFI mode, it might be more tricky. The easiest way is to remove (disconnect) the internal drive, and install the system into the pendrive. Then the EFI partition with be written to the correct drive.

The two systems described above will boot either in BIOS mode or UEFI mode. If you want an installed system to boot both in UEFI and BIOS mode, you can create it like I describe in the following links,

[Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
[Installation/UEFI-and-BIOS/stable-alternative](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative)

You can create encrypted home for an existing user, and you can create a new user with encrypted home according to the following link.

[EncryptedHome](https://help.ubuntu.com/community/EncryptedHome)

It might be a good idea to skip swap (to avoid wear) rather then fixing encrypted swap. You should not use unencrypted swap, because it is a security hole.

-o-

If you still want to use encrypted home in a persistent live system, please try to create a new user with encrypted home according to [the same link](https://help.ubuntu.com/community/EncryptedHome). Maybe it works better than I think. Anyway please let us know :-)

---

