---
title: "ntfs partition as /home/username and My Documents in Windows + Ubuntu"
date: 2007-07-14
forum: General Help
---

### Post by tk03759 on 2007-07-14
Okay, so I have a little bit of an issue here.

I just purchased a new 250GB Hard Drive. I split it, and installed ubuntu (with all it's necissary partitions) on one half, and left the other half as a FAT32 partition, hoping to be able to access and use it in both Windows and Ubuntu.

On a seperate 30GB hard drive, I have XP installed, with a My Documents folder filled with more than 10GB of files spanning from 2000 to 2007.

I got an idea that I might be able to use the FAT32 partition on my 250GB drive as a My Documents/home style folder for XP and Ubuntu.

I found this article on Microsoft's site explaining how to mount a drive to an empty folder in Windows, which even mentioned using a separate partition as the My Documents folder:
[http://support.microsoft.com/kb/307889]("http://support.microsoft.com/kb/307889")
The problem here is that you can only perform this type of mount in Windows if the drive is formatted as NTFS. I formatted it, moved all the contents in the My Documents folder to the drive, and mounted the drive as the My Documents folder in XP. It worked great.

I booted Ubuntu, and ran into problems even accessing the drive. I have ntfs-config installed, and my Windows Hard Drive is automatically mounting and I can access its files, but the My Documents partition on my 250GB drive won't even allow me to see its contents. It appears in the /media/sda4 mount point, but it appears as empty, and doesn't appear in Computer.

How should I format the drive and what might be a better option if I want to make the disk read-write in both OSs and still be able to mount it as My Documents in windows (so I don't lose shortcuts and such)?

Here's fdisk info if it helps. Sorry this was so long.

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          62      497983+  83  Linux
/dev/sda2              63         184      979965   82  Linux swap / Solaris
/dev/sda3             185       15381   122069902+  83  Linux
/dev/sda4           15382       30401   120648150    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40000020480 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           4       32098+  de  Dell Utility
/dev/sdb2   *           5        4862    39021885    7  HPFS/NTFS


PS. I read the following thread, but didn't quite find the answer I needed.
[http://ubuntuforums.org/showthread.php?t=219550 ]("http://ubuntuforums.org/showthread.php?t=219550")

---

### Post by jkwarras on 2007-07-14
You should have no problems accesing and writting to a ntfs partition in feisty. But you have, and I can only think in a format error, or something, so maybe you could do a scandisk on the partition and repair it.

Anyway, you could use a FAT32 or a EXT3 filesystem in that partition. Fat32 will give you no problem on both systems, and EXT3, if you install the ext3 driver for windows freely available on the net, you should not have problems.

BTW, you can move all your My documents to any location you want in windows. Just move it via right-click on explorer. For other options (like My music, blabla) you'll have to play with the registry, but it's easy. I don't remember how, because right now I don't use windows anymore (thanks you ubuntu), but google for it.

Hope it helps.

---

### Post by tk03759 on 2007-07-14
I had a disk check for the partition run this morning and told it to automatically fix errors and whatnot. I restarted to Ubuntu. The drive is showing in Computer, but is not mounted. I tried sudo mount /dev/sda4 from the terminal and this is what I got (I followed its instructions to get the followup information as well):

```
user@computer:~$ sudo mount /dev/sda4
Password:
mount: wrong fs type, bad option, bad superblock on /dev/sda4,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

user@computer:~$ dmesg | tail
[   46.397156] Bluetooth: RFCOMM socket layer initialized
[   46.397575] Bluetooth: RFCOMM TTY layer initialized
[   46.397583] Bluetooth: RFCOMM ver 1.8
[  208.388548] eth0: no IPv6 routers present
[  532.471166] NTFS driver 2.1.28 [Flags: R/O MODULE].
[  532.479149] NTFS-fs warning (device sdb2): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
[  532.520765] NTFS volume version 3.1.
[  611.836577] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[  611.862978] FAT: bogus number of reserved sectors
[  611.862990] VFS: Can't find a valid FAT filesystem on dev sda4
```

I really don't understand what's going on here... =/

---

### Post by merlinus on 2007-07-14
What is the output of:

```

sudo fdisk -l
cat /etc/fstab

```

-merlin

---

### Post by tk03759 on 2007-07-14
```
user@computer:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          62      497983+  83  Linux
/dev/sda2              63         184      979965   82  Linux swap / Solaris
/dev/sda3             185       15381   122069902+  83  Linux
/dev/sda4           15382       30401   120648150    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40000020480 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           4       32098+  de  Dell Utility
/dev/sdb2   *           5        4862    39021885    7  HPFS/NTFS
user@computer:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=b4451189-907c-4220-afa6-5a1a8af3721b / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda1 :
UUID=77be56c3-33e6-494e-b436-9a0697d59168 /boot ext3 defaults 0 2
# Entry for /dev/sda2 :
UUID=27cff265-76a9-49d4-bcf5-eeb7179d05ba none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/sda4 /media/sda4 vfat iocharset=utf8,umask=000 0 0
user@computer:~$ 

```

---

### Post by merlinus on 2007-07-14
/etc/fstab shows sda4 being mounted as vfat.  That is why you are getting some of the error messages.

You might try editing that line:

```

gksudo gedit /etc/fstab

```and changing the line to:

/dev/sda4 /media/sda4 ntfs defaults,locale=en_US.utf8 0 0

Then reboot.

-merlin

---

### Post by tk03759 on 2007-07-14
Okay. Now It's showing up in /media/sda4, but it's still coming up as emtpy. ("0 Items. 105.2GB") My files show up on it in windows, so I know they are there.

---

### Post by merlinus on 2007-07-14
OK -- some progress.

Now install the drivers so ubuntu can write to the partition:

```

sudo apt-get ntfs-3g ntfs-config

```Then go to Applications/System Tools/NTFS Configuration Tool and tick the appropriate boxes.

Restart and see what happens. Also, open Places/Home Folder and there may be an entry listed for the partition.

-merlin

---

### Post by tk03759 on 2007-07-14
> **merlinus said:**
> OK -- some progress.

Now install the drivers so ubuntu can write to the partition:

```

sudo apt-get ntfs-3g ntfs-config

```Then go to Applications/System Tools/NTFS Configuration Tool and tick the appropriate boxes.

Restart and see what happens. Also, open Places/Home Folder and there may be an entry listed for the partition.

-merlin

I'm assuming you meant "sudo apt-get install ntfs-3g ntfs-config" which I did and am restarting..


and.. it works! thankyou thankyou thankyou!!! =)

---

