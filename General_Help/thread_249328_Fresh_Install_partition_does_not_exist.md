---
title: "Fresh Install: partition does not exist?"
date: 2006-09-02
forum: General Help
---

### Post by ryedunn on 2006-09-02
Ive decided to get on the bandwagon and make the switch from Mandrake to Ubuntu.  Unfortunately Im having some small issues during the install Im hoping you can assist me with.

The install itself goes fairly well but when attempting to boot for the first time the system hangs just after
"Uncompressing Linux... Ok, Booting the kernel."
After about 5 minutes I get an error
"ALERT! /dev/hda5 does not exits. Dropping to a shell!"

I have tried almost every combination of partitioning that I can think of, letting Ubuntu take care of it with a swap and one big /
LVM, RAID (Which I really dont know much about) and I have tried setting the partitions up manually.n  Brand new 320GB drive.

100 MB /boot Primary Bootable
2 GB /     ext3
5 GB /tmp  ext3
5 GB /var  ext3
5 GB /usr  ext3
300G /home ext3
3 GB swap

The only thing I can think of is when booting right after 
Booting 'Ubuntu, kernel 2.6.15-26-server'  (yes I would like server)
root (hd0,0)

Filesystem type is ext2fs, partition type 0x83
Now is this wrong since all my partitions are ext3?

:confused: 
Looking for any help you can provide, 
Ryan

---

### Post by zxee on 2006-09-02
I don't think the problem is the filesystem 83 is linux, but having /usr and /var on seperate partitions while it should be doable might be causing problems. You didn't say what was contained in /dev/hda5 but it doesn't seem to be being mounted for boot and that is causing problems.

What drives and their types (ide, sata, ect) are in your system? 
Maybe check out the ubuntu install guides here: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by ryedunn on 2006-09-02
I have also tried to use the default install where there is just one huge partition on / and a 3.2 GB swap.  I can try that one again if you would like to know the exact error.

The drive is a Seagate 320GB EIDE HD 7200/16MB/ATA-100

I have read quite a few posts and docs but not the one you refered me to, so I will go start on that now.

---

### Post by ryedunn on 2006-09-02
just a guess, but couldnt grub be confused with the drive numbering?

---

### Post by ryedunn on 2006-09-02
I got it... it was /dev/hde but grub was pointing to hda for some reason

thnx

---

