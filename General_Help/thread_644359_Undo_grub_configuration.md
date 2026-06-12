---
title: "Undo grub configuration?"
date: 2007-12-18
forum: General Help
---

### Post by Hawk__0 on 2007-12-18
I have 2 drives, and I ran "setup (hdx)" where x is my drive (0 and 1).  
Now if i choose my windows drive (drive 1) , I see the beginning of when ubuntu would load (it says something like "Loading...." then it hangs.  a while later, I see "GRUB GRUB GRUB" endlessly repeating on my screen

is this because I ran setup (hd1)?
If so, how do I undo this?

---

### Post by Hawk__0 on 2007-12-18
bump (or how do I reinstall the windows bootloader? without reinstalling windows? ... or would I need the windows MBR? I confused.)

---

### Post by Hawk__0 on 2007-12-18
bump......

---

### Post by Hawk__0 on 2007-12-18
bump.....

---

### Post by mikewhatever on 2007-12-18
> **Hawk__0 said:**
> bump (or how do I reinstall the windows bootloader? without reinstalling windows? ... or would I need the windows MBR? I confused.)

Just for the record, Windows does not have an MBR, but does have a boot loader. For more info --> [http://users.bigpond.net.au/hermanzone/p6.htm](http://users.bigpond.net.au/hermanzone/p6.htm)

It is not enough to simply install Grub to hdx. Grub has a configuration menu on the linux partition. Here's the full path /boot/grub/menu.lst.

To reinstall Windows boot loader or Grub, use super grub CD [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html).

---

### Post by Hawk__0 on 2007-12-18
Okay I used the disc.  Now in grub, it doesn't boot windows.. it just flickers some text, then puts me back at the bootloader.

So I'm back in ubuntu now, and I tried to mount my windows drive.  I get this error while trying to do so now:

[IMG]http://img295.imageshack.us/img295/2355/errhg9.png[/IMG]

---

### Post by mikewhatever on 2007-12-19
While in Ubuntu, can you post the output of <sudo fdisk -lu> without the <>. Do you have the latest, 7.10, version of Ubuntu?

---

### Post by Hawk__0 on 2007-12-19
7.10, yes
```
Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x02e102e1

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   314102879   157051408+  83  Linux
/dev/hda2       314102880   320159384     3028252+   5  Extended
/dev/hda5       314102943   320159384     3028221   82  Linux swap / Solaris

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4eeb4eea

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63    61432559    30716248+   7  HPFS/NTFS

Disk /dev/sda: 512 MB, 512483328 bytes
16 heads, 63 sectors/track, 993 cylinders, total 1000944 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfb7afb7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             233      999935      499851+   6  FAT16

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x863a4fbb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *         538   488408129   244203796    7  HPFS/NTFS
steve@steve:~$ 

```

the 160GB drive is my ubuntu drive, the 30~GB drive is my windows partition on a separate disk.
ignore the last 2 drives (ones a USB drive, the other is an external drive)

---

### Post by mikewhatever on 2007-12-19
I don't know. fdisk shows no errors. What happens if you type <sudo mount /dev/hdb1> in a terminal?

---

### Post by Hawk__0 on 2007-12-19
=\
```
mount: can't find /dev/hdb1 in /etc/fstab or /etc/mtab

```
I'm not sure why it isn't in there...

---

### Post by mikewhatever on 2007-12-19
Have you tried mounting it from GUI, in other words, from the side pane? What does your fstab looks like? <sudo cat /etc/fstab>

To mount it manually, create a mount point <sudo mkdir /media/hdb1>.
Then mount <sudo mount -t ntfs /dev/hdb1 /media/hdb1>.

---

### Post by Hawk__0 on 2007-12-19
```
steve@steve:~$ **sudo mkdir /media/hdb1**
steve@steve:~$ **sudo mount -t ntfs /dev/hdb1 /media/hdb1**
Unexpected clusters per mft record (-128).
Failed to mount '/dev/hdb1': Invalid argument
The device '/dev/hdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
steve@steve:~$ **sudo rmdir /media/hdb1**
steve@steve:~$ 
```

```
steve@steve:~$ **cat /etc/fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=3d27f7f0-c4a3-4045-a629-9dd45b80cbe0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=548ac3b6-c02f-49e0-a81c-7547f76fef4a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
steve@steve:~$ 


```

```
steve@steve:~$ **cat /etc/mtab**
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/sda1 /media/disk vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree 0 0
/dev/sdb1 /media/Vault fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
/dev/hdc /media/cdrom0 iso9660 ro,nosuid,nodev,user=steve 0 0
steve@steve:~$ 

```

---

### Post by mikewhatever on 2007-12-19
Well, I googled the first error message, **Unexpected clusters per mft record (-128)**. It looks like it has something to do with corrupted boot sector. You might want to look at it. The first two results from the search seem to offer successful solutions.
[http://www.google.co.il/search?q=Unexpected+clusters+per+mft+record+(-128)&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.co.il/search?q=Unexpected+clusters+per+mft+record+(-128)&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

---

### Post by Hawk__0 on 2007-12-19
OK well i did everything i could with that "testdisk" program.
epic failure on my part.
I "ERASED" grub from the windows drive and put on ntloader, according to it, yet if i boot from that specific disk, I get an error: "grub hard disk error" message :(

---

### Post by Hawk__0 on 2007-12-19
bump

---

### Post by mikewhatever on 2007-12-20
How did you restore Windows boot loader? There are several ways to do it. Here's what I would've done.
1. Turn the computer off, disconnect all external HDDs to avoid confusion and then power up.
2. Try restoring Windows boot loader using Windows recovery console (fixmbr) or super grub disk.

---

### Post by Hawk__0 on 2007-12-20
I tried using windows xp's disc, but when I hit ... (F2?) It says "please insert disk into drive A:"
....the recovery disk or something.
Well, i have no floppys, or a recovery disk.  from what i've read I shouldn't be getting this error anyways =\

---

### Post by mikewhatever on 2007-12-20
[http://www.computerhope.com/issues/ch000627.htm](http://www.computerhope.com/issues/ch000627.htm)

I wasn't aware you had to press f2 for recovery console. How did you restore then?

---

### Post by Hawk__0 on 2007-12-21
I used the grub super disc

---

