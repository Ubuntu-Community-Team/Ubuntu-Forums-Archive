---
title: "unable to mount external HD"
date: 2008-07-08
forum: General Help
---

### Post by hellzkeeper1216 on 2008-07-08
I have a toshiba 100gb external harddrive. and i have been trying to extract the photos from it. i tried to mount it and force mount it but i can't seem to do it.

I used the lsusb command

Bus 002 Device 001: ID 0000:0000
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 002: ID 0930:a000 Toshiba Corp.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 003: ID 04f2:b008 Chicony Electronics Co., Ltd
Bus 003 Device 001: ID 0000:0000
jon@jon-laptop:~$

jon@jon-laptop:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30ad509f

Device Boot Start End Blocks Id System
/dev/sda1 * 1 23568 189309928+ 83 Linux
/dev/sda2 23569 24321 6048472+ 5 Extended
/dev/sda5 23569 24321 6048441 82 Linux swap / Solaris

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
jon@jon-laptop:~$


jon@jon-laptop:~$ tail -F /var/log/messages
Jul 8 18:25:23 jon-laptop kernel: [ 309.880849] sd 3:0:0:0: [sdb] Add. Sense: No additional sense information
Jul 8 18:25:23 jon-laptop kernel: [ 309.892934] sd 3:0:0:0: [sdb] Sense Key : No Sense [current]
Jul 8 18:25:23 jon-laptop kernel: [ 309.892943] Info fld=0x0
Jul 8 18:25:23 jon-laptop kernel: [ 309.892945] sd 3:0:0:0: [sdb] Add. Sense: No additional sense information
Jul 8 18:25:23 jon-laptop kernel: [ 309.905291] sd 3:0:0:0: [sdb] Sense Key : No Sense [current]
Jul 8 18:25:23 jon-laptop kernel: [ 309.905299] Info fld=0x0
Jul 8 18:25:23 jon-laptop kernel: [ 309.905302] sd 3:0:0:0: [sdb] Add. Sense: No additional sense information
Jul 8 18:25:23 jon-laptop kernel: [ 309.917381] sd 3:0:0:0: [sdb] Sense Key : No Sense [current]
Jul 8 18:25:23 jon-laptop kernel: [ 309.917390] Info fld=0x0
Jul 8 18:25:23 jon-laptop kernel: [ 309.917393] sd 3:0:0:0: [sdb] Add. Sense: No additional sense information
jon@jon-laptop:~$ sudo mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jon/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jon)
jon@jon-laptop:~$

jon@jon-laptop:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/hd-ntfs
ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.
jon@jon-laptop:~$


Any help would be great...

---

### Post by nikgare on 2008-07-10
HAs it worked under Ubuntu, or did you put the photos on using Windows/Mac?
Do you know the format of the drive?

---

### Post by hellzkeeper1216 on 2008-07-10
It has pictures from Windows Vista on it, and the drive is formatted in NTFS. I installed the package ntfs3 but it still wont mount.

---

### Post by hellzkeeper1216 on 2008-07-11
*bump* anyone? Bump.... plz.

---

### Post by treymul on 2008-07-11
Shouldn't you be trying to mount /dev/sdb?  I had an encrypted external harddrive that I had trouble mounting.  I created a file mount point:

mkdir /media/sdb

Then I mounted the drive (using fdisk to find it), from your fdisk it looks like /dev/sdb to me.

sudo mount /dev/sdb /media/sdb

That got me going, but I am new to linux, so thats all I know to do.

---

### Post by hellzkeeper1216 on 2008-07-11
I tried that and it told be that there isn't a valid partition to mount.

---

### Post by chris4585 on 2008-07-11
i suggest, installing mountpy

```
sudo apt-get install mountpy

sudo mountpy
```

to mount

if that doesnt work, dunno

---

### Post by nikgare on 2008-07-11
Isn't ntfs support already in the kernel now?
In which case installing ntfs3 might be confusing issues?
You could try booting from the LiveCD and seeing if the drive is recognised then?

---

### Post by hellzkeeper1216 on 2008-07-11
jon@jon-laptop:~$ sudo mountpy
/dev/sda1 seems to be already mounted on /                    
Found nothing to mount  

but when i go into the Computer, and double click the drive it says.
"Unable to mount Location"
"Can't mount file"
I just want to say thanks for all the help thus far. I appreciate it. I need some of these pictures for a client.

---

### Post by linyanam on 2008-11-12
Check this bug report and fix.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264789/comments/46](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264789/comments/46)

---

