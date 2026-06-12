---
title: "urgent!  how to fix linux boot sector?"
date: 2007-04-30
forum: General Help
---

### Post by rygar on 2007-04-30
i screwed up my computer and i need to work on my finals!  can someone please help me?

to the point:

my linux partition's boot sector was overwritten with an ntfs one.  how do i repair it to an ext3 partition?  please assume ignorance on my part, i just installed ubuntu a few days ago and am not familiar with much of it.

explanation:

i recently partitioned my hard drive to have XP on a 30 gb partition (installed first), Vista on a 40 gb partition (installed second), and ubuntu on a 25 gb partition (installed third).  i also have an ntfs formatted 500gb external hard drive.b

my external USB drive wasn't working in linux.  it told me the disk was scheduled for check and to boot into windows TWICE.  it didn't work, and i couldn't access my external usb from either windows or linux.

foolishly of me, i accidentally ran a 'fixboot' on the linux partition from a windows recovery console, thinking it was my external hard drive.  it screwed up the boot sector, so my linux partition is being shown as an ntfs one.

i then scanned and fixed my external usb and boot to linux from cd.  gparted shows:

/dev/sda1 ntfs /media/XP (29.29gb)
/dev/sda2 extended (40.13gb)
-->  /dev/sda5 ntfs /media/Vista (39.06gb)
--> /dev/sda6 linux-swap (1.07gb)
/dev/sda3 ntfs(23.73gb)

i/dev/sda3 should be my linux partition, paired with the swap from /dev/sda6

the linux boot cd can read my XP and Vista drives fine, as well as the external hard drive.

booting from my hard drive brings me to grub and gives me an error 17.

how do i repair the boot sector on /dev/sda3 ?

also, neither linux nor windows let me properly unmount my external hard disk.  could this be the cause of the 'corruption' on my (new) external usb drive?  what can i do about it?  i'm afraid of losing data.

any help is greatly appreciated!

thanks!
JEFF

---

### Post by khughitt on 2007-04-30
> booting from my hard drive brings me to grub and gives me an error 17.

You mean your internal drive? When you turn on your pc, does windows boot manager come up? or does grub?

What is output when you run the command **sudo /sbin/fdisk -l** when you boot the livecd? Also, what does your **/boot/grub/menu.lst** file look like?

---

### Post by medya on 2007-04-30
give [this a try ]("http://blog.shevin.info/2007/04/messed-up-boot-loader-dont-worry.html")

---

### Post by rygar on 2007-04-30
Since I installed Ubuntu last, GRUB is my boot manager.

When i boot from my internal disk (ie start my comptuer), GRUB shows up and gives me an error 17.  i've got the suspicion that i could rewrite the MBR to restore windows boot loader and boot into windows, but that won't help me fix my linux partition.

sudo /sbin/fdisk -l gives me this:

```
ubuntu@ubuntu:/$ sudo /sbin/fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        9063    42082267+   f  W95 Ext'd (LBA)
/dev/sda3            9064       12161    24884685   83  Linux
/dev/sda5            3825        8923    40957686    7  HPFS/NTFS
/dev/sda6            8924        9063     1124518+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS

```

/boot/grub/menu.lst is not there (because i'm booting from the cd?)

```
ubuntu@ubuntu:/boot$ cd grub
bash: cd: grub: No such file or directory
ubuntu@ubuntu:/boot$ ls
abi-2.6.20-15-generic             memtest86+.bin
config-2.6.20-15-generic          System.map-2.6.20-15-generic
initrd.img-2.6.20-15-generic.bak  vmlinuz-2.6.20-15-generic
ubuntu@ubuntu:/boot$ 

```

---

### Post by rygar on 2007-04-30
> **medya said:**
> give [this a try ]("http://blog.shevin.info/2007/04/messed-up-boot-loader-dont-worry.html")

i haven't tried it, but i don't think that is my problem.  i did not change my MBR (fixmbr).  I changed only the boot sector on a particular partition (fixboot).  i dont think GRUB would even load if i had corrupted the MBR, no?

---

### Post by rygar on 2007-04-30
FIXED!  after exploring different commands I found one that did what I want to do.

sudo e2fsck -f /dev/sda3

yes to everything, and grub loads/ubuntu loads fine!  hopefully this thread will help someone else with my problem.

though i would still like to know about unmounting my external usb to prevent corruption, ill probably open another thread for that.

thanks all!

---

### Post by merlinus on 2007-04-30
Indeed, this has just saved me from having to a complete reinstallation!

Whew!!!

It should be posted as a sticky in this forum.

Thanks so much.

-merlin

---

