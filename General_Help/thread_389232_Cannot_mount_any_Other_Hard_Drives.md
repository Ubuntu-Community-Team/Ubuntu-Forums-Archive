---
title: "Cannot mount any Other Hard Drives"
date: 2007-03-20
forum: General Help
---

### Post by regomodo on 2007-03-20
Hi, i'm not a total linux newbie but i am at my wits end trying to get Ubuntu to find and mount my 2 extra internal HDDs.I am using Ubuntu that i downloaded from the main site last night and have run all the updates.
 
I currently have 3 HDDs. 2 IDE's and one SATA. I am booting off the master IDE and the other 2(Maxtor 200GB IDE and Maxtor 500GB sata) have various partitions. One is in ext3, one in ntfs and the other in fat32.

With fdisk i can see that all my partitions are there so i use suitable mkdir commands for these partitons and edit the fstab. Well, that didn't work. I got it to work with slack a long time ago (albeit without sata) so i looked at the online help documents. Exactly as what i did. Must stress, it will not find the ext3 partiton i just created with knoppix's QTPARTED.

Saw on the Ubuntu help that i can mount windows partitions using "System>Administration>Disk", well, that path doesn't exist. I have accidentally wiped my xp install partition using a certain command that i forget whilst following another guide (it had an "fs" in there somewhere).

I am currently returning to linux for the second time (gave up with slackware due to lack of package management, and arklinux as it had no benefit) and saw the new revolution with Ubuntu. Its good just been setting it up for a while now (spent the last 3 days to get xubuntu to work as i want minus the HDDs), configuring nvclock (still no idea how to install nvidia driver with coolbits), my widescreen lcd, and cd burning software (xfburn is tosh).

Despite me wanting this to work i feel i may return to xp again despite it's bloated crapness.

Any help would be appreciated, and yes, i have used the search function.

Cheers

---

### Post by taurus on 2007-03-20
What's the output of this command from a terminal?

```
sudo fdisk -l
```
Or use this guide.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by regomodo on 2007-03-20
Disk /dev/hdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       14338   115169953+  83  Linux
/dev/hdc2           14339       14946     4883760    5  Extended
/dev/hdc5           14339       14946     4883728+  82  Linux swap / Solaris

Disk /dev/hdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       24321   195358401   83  Linux

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9607    77168196    7  HPFS/NTFS
/dev/sda2            9608       35716   209720542+   5  Extended
/dev/sda5            9608       35716   209720511    7  HPFS/NTFS

Disk /dev/sdb: 1014 MB, 1014751744 bytes
32 heads, 61 sectors/track, 1015 cylinders
Units = cylinders of 1952 * 512 = 999424 bytes

   Device Boot      Start         End      Blocks   Id  System



Bit confused why /dev/sdb has no usuable partitions. Not interested at the moment

---

### Post by taurus on 2007-03-20
So you want to mount /dev/hdd1, /dev/sda1, & /dev/sda5.  From a terminal, edit /etc/fstab with

```
gksudo gedit /etc/fstab
```
and add these three lines to the end of it.

```
/dev/hdd1   /media/hdd1   ext3   defaults   0   1
/dev/sda1   /media/sda1   ntfs   nls=utf8,umask=0222   0   0
/dev/sda5   /media/sda5   ntfs   nls=utf8,umask=0222   0   0
```
Save it.  Then, create those three new mount points and mount them.

```
sudo mkdir /media/hdd1 /media/sda1 /media/sda5
sudo mount -a
df -h
```

---

### Post by regomodo on 2007-03-20
cheers for that.

I had just sorted the ext3 partition but couldn't get the permissions right.

Just done what you said got an error for sda1. Think it's because i chewed it up from a previous attempt. I'll format that part first and try again.

jon@jon-desktop:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

jon@jon-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdc1             109G  2.6G  101G   3% /
varrun               1014M   80K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
procbususb             10M  140K  9.9M   2% /proc/bus/usb
udev                   10M  140K  9.9M   2% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   18M  997M   2% /lib/modules/2.6.17-11-generic/volatile
/dev/sdb              966M  4.0K  966M   1% /media/floppy1
/dev/hdd1             184G  174G  631M 100% /media/SlaveHD
/dev/hdd1             184G  174G  631M 100% /media/hdd1
/dev/sda5             201G  175G   26G  88% /media/sda5

---

### Post by taurus on 2007-03-20
Make sure /dev/sda1 is ntfs and looks like you mount /dev/hdd1 to two different mount points at the same time!

```

dev/hdd1 184G 174G 631M 100% /media/SlaveHD
/dev/hdd1 184G 174G 631M 100% /media/hdd1

```
Do you still want to write to /dev/hdd1?  You need to unmount one of them and then change the ownership from root to **jon**, your login name, so you can write and delete stuff from it.

```
sudo umount /media/SlaveHD
sudo chown -R **jon**:**jon** /media/hdd1
ls -la /media
```

p.s.  If you ahve two entries in /etc/fstab for /dev/hdd1, you need to remove one of them, probably the /media/SlaveHD.

---

### Post by regomodo on 2007-03-20
hmm, i don't know why it did that. I removed previous fstab entries and rmdir directories i had made.

Just looked at fstab and they aren't there.

I'm going to remove sda5 as it's a copy of hdd1 just in fat32 format

I'm sure i can find out how to sort it out but i just accidentally removed the trash icon. Any ideas?


Also, cheers for the help to get my drives working. Just now have to figure out how to save my nvclock settings and to get xilinx 7 to install without it giving up halfway through.
Many thanks, sure i'll get help from you again in the near future.

---

