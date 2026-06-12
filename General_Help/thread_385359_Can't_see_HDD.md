---
title: "Can't see HDD"
date: 2007-03-15
forum: General Help
---

### Post by klipart on 2007-03-15
Recently my computer booted up and did a disk check like it does every 30 times it turns on.  I was moving my keyboard and I think I may of hit a button or it might of been some crazy coincidence but my computer displayed and error message and rebooted.  It booted in to Ubuntu no problem except for the fact I cant access my hard drive anymore.  The icon on my desktop disappeared and when I go into the device manager I can see it there.  Does anyone know how I can get it back?

---

### Post by taurus on 2007-03-15
Which harddrive?  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by klipart on 2007-03-15
I have two hard drives but the main one is 200gB and has ubuntu and what is left of windows on it and it is the one that has disappeared.  I can still see it in the device manager but here is the output from that terminal command:

fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by klipart on 2007-03-15
I'm sorry I am a n00b at this i put -1 instead of -l here is the -l one:
andy@andy-desktop:~$ sudo fdisk -l

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       15298   122881153+   7  HPFS/NTFS
/dev/hda2           15299       15363      522112+  82  Linux swap / Solaris
/dev/hda3           15364       24321    71955135   83  Linux

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4865    39078081    7  HPFS/NTFS
Note: sector size is 2048 (not 512)

Disk /dev/sda: 30.0 GB, 30005819392 bytes
255 heads, 63 sectors/track, 911 cylinders
Units = cylinders of 16065 * 2048 = 32901120 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           3       96264    0  Empty
/dev/sda2               4         912    29206170    b  W95 FAT32

---

### Post by taurus on 2007-03-15
You mean /dev/hda1 doesn't mount at all at boot!  What is the output of this command from a terminal?

```
cat /etc/fstab
```

---

### Post by klipart on 2007-03-15
I thought it just vanished, is there a way to make it mount again and or make it mount at boot?  Here is what you requested:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=24203391-41a8-40d9-b8bb-e3280a0ef737 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=01C457F2B5865B80 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=627462C474629B15 /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=fd7962d0-a7a5-41d0-b828-9e622a2705d7 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by taurus on 2007-03-15
Edit /etc/fstab

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
and replace this line (for /dev/hda1)

```
UUID=01C457F2B5865B80 /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
```
with this one.

```
/dev/hda1    /media/hda1    ntfs    defaults,nls=utf8,umask=007,gid=46    0    0
```
Save it and reboot.  Now, do you see /dev/hda1 in /media/hda1?

```
df -h
```

---

### Post by klipart on 2007-03-15
I still can't see it I changed that line to exactly what you put, do I need a UUID term in the new one?

---

### Post by taurus on 2007-03-15
Can you post your /etc/fstab and the output of this commnad here?

```
cat /etc/fstab
df -h
```
Otherwise, you can make an entry for /dev/hda1 to look like this in /etc/fstab.

```
/dev/hda1    /media/hda1    ntfs    nls=utf8,umask=0222    0    0
```

---

### Post by Malac on 2007-03-15
This might be unrelated but does the drive appear again after you run this:
```
sudo /etc/init.d/dbus restart
```

---

### Post by klipart on 2007-03-15
Here is the thing you asked for:

andy@andy-desktop:~$ gksudo gedit /etc/fstab
(gedit:4806): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
andy@andy-desktop:~$ gksudo gedit /etc/fstab

(gedit:4835): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
andy@andy-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=24203391-41a8-40d9-b8bb-e3280a0ef737 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
/dev/hda1    /media/hda1    ntfs    defaults,nls=utf8,umask=007,gid=46    0    0
# /dev/hdb1
UUID=627462C474629B15 /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=fd7962d0-a7a5-41d0-b828-9e622a2705d7 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
andy@andy-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              68G  4.9G   60G   8% /
varrun                252M   60K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb             10M  116K  9.9M   2% /proc/bus/usb
udev                   10M  116K  9.9M   2% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   20M  233M   8% /lib/modules/2.6.17-11-generic/volatile
/dev/hdb1              38G  8.0G   30G  22% /media/hdb1

---

### Post by taurus on 2007-03-15
See if you can mount it by hand from a terminal first.

```
sudo mount -t ntfs /dev/hda1 /media/hda1 -o nls=utf8,umask=0222
df -h
```

---

### Post by klipart on 2007-03-15
I couldn't mount it, here is the output:

andy@andy-desktop:~$ sudo mount -t ntfs /dev/hda1 /media/hda1 -o nls=utf8,umask=0222
Password:
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by taurus on 2007-03-15
Do you have Windows on /dev/hda1?  If you do, may want to boot into Windows and check the partition to make sure it is in a good working condition.

---

### Post by klipart on 2007-03-15
windows doesnt work anymore unfortunately, but ill borrow my friends external hard drive inclosure and test it

---

### Post by taurus on 2007-03-15
So Windows on that partition crashed and I assume you want to recover data on it!  Did it ever work before in Ubuntu, mounting it?

---

### Post by klipart on 2007-03-15
You are correct with the windows assumption but I was still able to access that drive before this fiasco with Ubuntu, I am at a loss as to why Ubunutu can see it in the device manager and read and write stuff to the "file system" that is on that drive but it cannot access the rest of it.

---

### Post by Malac on 2007-03-16
Try a slight alteration to taurus suggestion
sudo mount /dev/hda1 /media/hda1
df -hwithout any options and see if it detects the filesystem anyway.

---

### Post by klipart on 2007-03-16
The mount didn't cause an error message to come up, rather nothing came up at all I dont know if that is normal.  I still can't see the HDD though, here is the output from the  df -h:

andy@andy-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              68G  4.9G   60G   8% /
varrun                252M   60K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb             10M  116K  9.9M   2% /proc/bus/usb
udev                   10M  116K  9.9M   2% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   20M  233M   8% /lib/modules/2.6.17-11-generic/volatile
/dev/hdb1              38G  8.0G   30G  22% /media/hdb1
/dev/hda1              11M  6.8M  3.4M  67% /media/hda1

---

### Post by Malac on 2007-03-16
Just a quick check that's it's not something else.
It may sound patronising but can you open gconf-editor and navigate to /apps/nautilus/desktop and check that volumes_visible is ticked. :)
It might be your gconf got screwed up.

---

### Post by klipart on 2007-03-16
I tried that and unfortunately it didn't work.  I tried to type in this command: "mount point /dev/hda3 /media/hda2" and it says "mount: only root can do that".  Does that mean it might work if i can be "root"?

---

### Post by taurus on 2007-03-16
> **klipart said:**
> I tried that and unfortunately it didn't work.  I tried to type in this command: "mount point /dev/hda3 /media/hda2" and it says "mount: only root can do that".  Does that mean it might work if i can be "root"?

It means that you have to run the command with sudo in front of it.

```
sudo mount /dev/hda1 /media/hda1
```

---

### Post by klipart on 2007-03-16
When I tried with Sudo it said this : sudo: point: command not found

---

### Post by taurus on 2007-03-16
What is the exact command that you ran?

---

### Post by Malac on 2007-03-16
klipart, you are typing in the wrong command:

It should be ```
**sudo mount /dev/hda1 /media/hda1**
```
There is no "point" in it.

---

