---
title: "external hard drive help?"
date: 2008-02-18
forum: General Help
---

### Post by evilbuntu on 2008-02-18
hello i recently purchased a simpletech 320 gig external HD from best buy

it will not auto mount, 
this is my fdisk -l info,

Disk /dev/sdb: 320.0 GB, 320072932864 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x63c683cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS


 does anyone know what i will have to type into ect/fstab file to get it to mount and do so every time i boot? i only wish to use it as external storage, not to boot or auto back up

thanks in advance, this is part of my college senior project, so any help is greatful

also could you tell me why i am puting in what i am putting in so i may explain it in my report (how i am getting the info for the hard drive code and why i am placing it there?) thanks again

---

### Post by fritogotlayed on 2008-02-18
Are you using the desktop version of Ubuntu or Server...  On my Desktop version the automount works pretty easily. 

You may want to look at /etc/fstab though. I'm not that familiar with it off the top of my head but maybe this will help you. [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by evilbuntu on 2008-02-18
i apologize its server

---

### Post by fritogotlayed on 2008-02-18
Cool, first off I haven't done this in forever so I may be a little off. Last time I had to do this was in FreeBSD 5 so... 

1.) Make a directory to mount your drive to
sudo mkdir /media/Chunky

2.) Make a backup of your fstab
sudo cp /etc/fstab /etc/fstab_backup

3.) Edit your fstab
sudo nano /etc/fstab

4.) make your edits
/dev/sdb   /media/Chunky   (filesystem)auto?    (options)default? 0 0

5.) mount
mount  (not sure if thats the command that automounts)

---

### Post by fritogotlayed on 2008-02-18
mount /dev/sdb

---

### Post by evilbuntu on 2008-02-18
its now telling me only root can mount it on media?

any suggestions

thank you so much for the help so far

---

### Post by fritogotlayed on 2008-02-18
Not a problem.  

1.) sudo mount /dev/sdb
2.) change your fstab options to include "user"

ex
rw[read / write],user[allows users to mount drive],auto[auto mounts],exec[allows binaries to run on this drive]


Note: you'll have to provide these without spaces, ex. rw,user,auto,exec


Hope that helps. You can get a overview of all those options at the URL above. Let me know if that helps.

---

### Post by fritogotlayed on 2008-02-18
I should note that you can do EITHER 1 OR 2...  sorry for the confusion there. Sometimes I get ahead of myself.

---

### Post by evilbuntu on 2008-02-18
man your gonna hate me'

now it says to specify file system type?

im taking it means fat or ntfs correct? how would i do this?

by the way you are an awsome help, im pretty new to this stuff with linux

---

### Post by fritogotlayed on 2008-02-18
Haha, we're all new at some point. I'm only about a year in. 

Yes, its asking for the file system type of the drive. It looks to me that the drive is formatted as NTFS so you may want to try that instead of auto. 


/dev/sdb /media/Chunky ntfs rw,user,auto,exec 0 0

---

### Post by evilbuntu on 2008-02-18
thanks for understanding

now im having more troubles?

this is what it says

evilbuntu@evilbuntu:~$ sudo mount /dev/sdb

mount: you must specify the filesystem type
evilbuntu@evilbuntu:~$ 
evilbuntu@evilbuntu:~$  sudo mount /dev/sdb
[mntent]: line 11 in /etc/fstab is bad
mount: can't find /dev/sdb in /etc/fstab or /etc/mtab
evilbuntu@evilbuntu:~$ 


this is my fstab


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5a1b7614-7ea0-43e8-9bea-efeccbdac0b4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=e8a95846-bbb2-4a88-9599-bd4afc22edb3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec  0       0
/dev/sdb        /media/FTP ntfs     auto    rw,user,auto,exec    0       0

im beginning to get a bit worried, also i changed the name form chunky to ftp for my own ease

---

### Post by fritogotlayed on 2008-02-18
haha, not a problem. You just had an extra item in your fstab line.

replace
"/dev/sdb /media/FTP ntfs auto rw,user,auto,exec 0 0" 
with 
"/dev/sdb /media/FTP ntfs rw,user,auto,exec 0 0"


If you'll notice the fstab file is space delimited. You simply had an extra argument that mount was barfing over.

---

### Post by evilbuntu on 2008-02-18
evilbuntu@evilbuntu:~$ sudo mount /dev/sdb
NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
evilbuntu@evilbuntu:~$ 

lol, could it be fat and not ntfs?

---

### Post by fritogotlayed on 2008-02-18
true, try vfat in place of ntfs

---

### Post by evilbuntu on 2008-02-18
evilbuntu@evilbuntu:~$ sudo mount /dev/sdb
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

evilbuntu@evilbuntu:~$ 


didnt work, im lost an ideas. maybe there is more info i could send your way i didnt yet?

is it dev/sdb or sdb1?

---

### Post by fritogotlayed on 2008-02-18
Wow, yea, I'm a tard. You definitely need the number on there, sdb1. *shakes head* Try that. 

Theres also a thread here with someone having a similar issue. 
[http://ubuntuforums.org/showthread.php?t=700564](http://ubuntuforums.org/showthread.php?t=700564)

---

### Post by bodhi.zazen on 2008-02-18
If you want read-write access you need ntfs-3g

```
sudo apt-get install ntfs-3g
```

Then the line in fstab should read :

> /dev/sdb1 /media/FTP  ntfs-3g  auto,users,uid=1000,gid=100,umask=007  0 0

If you do not need rw (ie ro) you can use the ntfs driver (rather then ntf-3g)

vfat will not work.

make sure the mount point exists ```
sudo mkdir /media/FTP
```

---

### Post by evilbuntu on 2008-02-18
in my fdisk list it says its sdb not sdb1, does it make the differance?

do i do the mount code after that?

---

### Post by evilbuntu on 2008-02-18
says this if i try and mount sdb1

evilbuntu@evilbuntu:~$ sudo mount /dev/sdb1
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/FTP -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/FTP ntfs-3g defaults,force 0 0

---

### Post by evilbuntu on 2008-02-18
anyone left?

---

### Post by evilbuntu on 2008-02-18
still looking for any help please

---

### Post by Yellow Pasque on 2008-02-18
Ideally, you would load the drive in Windown and unmount it properly there. If that's not plausible, use this:
```
sudo mount -t ntfs-3g /dev/sdb1 /media/FTP -o force
```

---

### Post by bodhi.zazen on 2008-02-18
Well, this is a problem of using NTFS if you do not have Windows ...

IMO, best is to boot to windows and let windows fix the problem.

Even better, convert the partition to linux native, ie ext3, reiserfs, XFS, JFS ....

If you do not have windows, the answer is in your error message :

> Choice 2: If you don't have Windows then you can use the 'force' option for
your own responsibility. For example type on the command line:

mount -t ntfs-3g /dev/sdb1 /media/FTP -o force

Or add the option to the relevant row in the /etc/fstab file:

/dev/sdb1 /media/FTP ntfs-3g defaults,force 0 0

So, you can try :

```
sudo mount -t ntfs-3g /dev/sdb1 /media/FTP -o force
```

Or edit fstab as advised.

Be warned, this may or may not cause data loss ...

---

### Post by evilbuntu on 2008-02-18
what is wondown

is it some sort of windows emulator for linux?

---

### Post by Yellow Pasque on 2008-02-18
No, it was a typo for 'Windows'.

---

### Post by evilbuntu on 2008-02-18
> **bodhi.zazen said:**
> Well, this is a problem of using NTFS if you do not have Windows ...

IMO, best is to boot to windows and let windows fix the problem.

Even better, convert the partition to linux native, ie ext3, reiserfs, XFS, JFS ....

If you do not have windows, the answer is in your error message :



So, you can try :

```
sudo mount -t ntfs-3g /dev/sdb1 /media/FTP -o force
```

Or edit fstab as advised.

Be warned, this may or may not cause data loss ...

in theory could i put the hard drive on my winows machine get it set up and then transfer it to my linux machine?

---

### Post by bodhi.zazen on 2008-02-18
> **evilbuntu said:**
> in theory could i put the hard drive on my winows machine get it set up and then transfer it to my linux machine?

Yes, I would advise that.

Even better, put the drive in your Windows machine, pull the data off, reformat the drive to linux native file system, restore data :twisted:

---

### Post by evilbuntu on 2008-02-18
i have no data on the drive

also  what is this linux native file system

---

### Post by fritogotlayed on 2008-02-18
Most default to ext3 if I'm not mistaken.

---

### Post by bodhi.zazen on 2008-02-18
> **evilbuntu said:**
> i have no data on the drive

also  what is this linux native file system

If you have no data on the drive, just reformat it to EXT3.

---

### Post by evilbuntu on 2008-02-19
i dont really know how to format in linux, i am very new to this OS

right now i am looking at soemthing called Qparted

---

### Post by bodhi.zazen on 2008-02-19
You can either do it from the command line or with a gui.

From the command line :

```
mkfs.ext3 /dev/sdb1
```

To do it with a gui, install gparted.  Then :

```
gksu gparted
```

---

### Post by articpenguin on 2008-02-20
ext3 does not scale well with a lot of files in a directory. It takes my computer 43 secs to find 2k files. But with JFS it took 12 secs. I think JFS is faster with directory looks up because of its B+ tree

---

### Post by bodhi.zazen on 2008-02-20
> **articpenguin said:**
> ext3 does not scale well with a lot of files in a directory. It takes my computer 43 secs to find 2k files. But with JFS it took 12 secs. I think JFS is faster with directory looks up because of its B+ tree

There is often a lot of hype regarding file systems. Here is a link if your are interested in reviewing the pros and cons of the major file systems :

[http://www.linux.com/feature/31939](http://www.linux.com/feature/31939)

---

