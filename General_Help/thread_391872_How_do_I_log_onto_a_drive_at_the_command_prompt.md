---
title: "How do I log onto a drive at the command prompt?"
date: 2007-03-23
forum: General Help
---

### Post by ACGilbert on 2007-03-23
Noob here with a really silly question.
I'm at the terminal prompt in my home directory and I want to go to another physical drive and work with the directories and files there.
For the life of me I can't figure this out!
it is /media/sdb5 and it is called Disk2_Vol1
Can't believe I've been using Ubuntu 6 months and haven't come across this.
This came about because I created a folder there and now I can't put anything in it because I don't have permission???
Right click and properties permissions tab has everything all grayed out.
Trying to do a chmod from the command line, but can' figure out the linux version of the old DOS C:, D:, etc.
Duh!
Thanks in advance,
AC

---

### Post by taurus on 2007-03-23
What is the filesystem of /dev/sdb5?  If you want to change to /media/sdb5 from a terminal, use the cd command.

```
cd /media/sdb5
ls -la
```

---

### Post by ACGilbert on 2007-03-23
Thanks for the reply Taurus,

I'm sitting at root of sda6.
cd /media/sdb5 gets me "command not found".
sdb5 is formatted as FAT.
I want to use it for both Linux and Windoze.
It is named Disk2_Vol1, but cd /Disk2_Vol1 gets me "no such file or directory".
I've got to be missing something incredibly simple.
I just trying to copy some files from a laptop that won't boot to my Ubuntu desktop.
Knoppix Live 5.1.1 is running on the laptop.

AC

P.S. I'll be away for the weekend and will check back here Sunday night or Monday morning.

---

### Post by taurus on 2007-03-23
Can you post the outputs of these commands from a terminal/prompt?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by ACGilbert on 2007-03-25
Taurus,

Here's the output of those commands on the ubuntu desktop.

fdisk -l

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9182    73754383+   7  HPFS/NTFS
/dev/sda2            9183       27532   147396375    f  W95 Ext'd (LBA)
/dev/sda5            9183        9444     2104483+  82  Linux swap / Solaris
/dev/sda6            9445       12055    20972826   83  Linux
/dev/sda7           12056       18583    52436128+  83  Linux
/dev/sda8           18584       27532    71882811   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       19457   156280320    f  W95 Ext'd (LBA)
/dev/sdb5               2       19457   156280288+   b  W95 FAT32

cat /etc/fstab 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=d6af429f-b1cf-497e-be8a-c6a007c99e08 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=9068156968154EFA /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=59692479-ba4f-4717-94f3-4f7d39b11c59 /media/sda6     ext3    defaults        0       2
# /dev/sda7
UUID=aa7a05ac-bf7d-4bc8-b7f9-3c56dcf376bb /media/sda7     ext3    defaults        0       2
# /dev/sdb5
UUID=0281-0283  /media/sdb5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=6763bb5b-4a42-430c-bfd3-5f35da18b96d none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8              68G  2.3G   62G   4% /
varrun                506M   88K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb             10M  168K  9.9M   2% /proc/bus/usb
udev                   10M  168K  9.9M   2% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   18M  489M   4% /lib/modules/2.6.17-11-386/volatile
/dev/sda1              71G   36G   35G  51% /media/sda1
/dev/sda6              20G  3.0G   16G  16% /media/sda6
/dev/sda7              50G  183M   47G   1% /media/sda7
/dev/sdb5             149G   80K  149G   1% /media/sdb5

My goal is to use Knoppix on my Laptop and be able to drag and drop Windows NTFS files onto the FAT drive (sdb5) on my desktop using my LAN. Does that seem like a reasonable way to do this? The laptop can't burn CDs or DVDs.

OBTW!
Today I can actually get to the /media/sdb5 with the CD command -- go figure!

---

