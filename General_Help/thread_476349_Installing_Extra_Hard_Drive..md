---
title: "Installing Extra Hard Drive."
date: 2007-06-17
forum: General Help
---

### Post by bilbobagins on 2007-06-17
Hi can anyone give me instruction on how to get a 250Gig H/D install onto Feisty , this will be just for file storage and no O/S install. Have looked through the forums and find plenty on twin drives and dual booting,but I`m 110%feisty here in fact 2 0f 3 pc`s here are Ubuntu ! so can anyone point me in right direction on this one.
Oh at the moment its formated ext3 is recognized by system but cant write to it and cant change permissions looks like a command line job and thats were i fall down cos i ain't that clever,:(
                                                                    thanks.jon

---

### Post by dreadlord_chris on 2007-06-17
> **bilbobagins said:**
> Hi can anyone give me instruction on how to get a 250Gig H/D install onto Feisty , this will be just for file storage and no O/S install. Have looked through the forums and find plenty on twin drives and dual booting,but I`m 110%feisty here in fact 2 0f 3 pc`s here are Ubuntu ! so can anyone point me in right direction on this one.
Oh at the moment its formated ext3 is recognized by system but cant write to it and cant change permissions looks like a command line job and thats were i fall down cos i ain't that clever,:(
                                                                    thanks.jon

Let's see if we can get ya fixed up. Need you to post the output of 2 commands for me. From the terminal type:
```

sudo fdisk -l

```
This will list the partitions that your OS *sees*

next:
```

cat /etc/fstab

```
This will show the drives/partitions that your OS knows of and (generally) mounts at boot.


Post the results of those 2 commands and we'll move to the next part.

---

### Post by bilbobagins on 2007-06-17
jonathan@jonathan-desktop:~$ sudo fdisk -l
Password:
sorry for delay
Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19266   154754113+  83  Linux
/dev/sda2           19267       20023     6080602+   5  Extended
/dev/sda5           19267       20023     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux
jonathan@jonathan-desktop:~$ 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=72a78e4d-6a9e-470d-9c2d-9f2b81386595 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=7a0b082c-9422-4ca2-b888-e4a82d8356e9 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
jonathan@jonathan-desktop:~$ 
 hope thats ok.

---

### Post by steveneddy on 2007-06-17
This issue was addressed [here]("http://ubuntuforums.org/showthread.php?t=199511") - just follow the links from aysiu.

It worked for me.

---

### Post by H.E. Pennypacker on 2007-06-17
I am assuming you have a desktop, since laptops take only a single hard drive, and I am also assuming that we are not dealing with an external hard drive.  If that is the case, add the new hard drive as slave, and Ubuntu should recognize it the next time you start up. 

Start off by installing the hard drive:

[http://www.ehow.com/how_6030_install-second-hard.html](http://www.ehow.com/how_6030_install-second-hard.html)

If you have any subsequent problems, let us know.

---

### Post by dreadlord_chris on 2007-06-17
> **bilbobagins said:**
> jonathan@jonathan-desktop:~$ sudo fdisk -l
Password:
sorry for delay
Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19266   154754113+  83  Linux
/dev/sda2           19267       20023     6080602+   5  Extended
/dev/sda5           19267       20023     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux
jonathan@jonathan-desktop:~$ 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=72a78e4d-6a9e-470d-9c2d-9f2b81386595 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=7a0b082c-9422-4ca2-b888-e4a82d8356e9 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
jonathan@jonathan-desktop:~$ 
 hope thats ok.

well... there ya go - you need to make a mount point & add it to fstab...
Your device socket is **/dev/sdb1**, so let's get to it: first the mount point - you need to pick a NAME. From here on replace NAME with what you chose...
```

sudo mkdir /media/NAME
ls -l /dev/disk/by-uuid/

```
from the last commands output look for the line that ends with /sdb1 and copy the long string that comes before the ->
i.e.
```

lrwxrwxrwx 1 root root 10 2007-06-16 15:49 efe89fd9-58ab-456c-9881-528a9149e3c7 -> ../../sdb1

```
you would copy **efe89fd9-58ab-456c-9881-528a9149e3c7**, it's called the UUID. Now edit fstab as **root**
```

gksudo gedit /etc/fstab

```

At the bottom add the following 2 lines - replacing <<UUID>> with the UUID copied earlier, and NAME with the mount point you picked:
```

# /dev/sdb1
UUID=<<UUID>> /media/NAME ext3 nouser,defaults,noatime,auto,rw,dev,exec,suid 0 2

```
save the file. Now back in the terminal:
```

sudo mount -a

```
if you get any errors post back....
Otherwise you're good to go...

---

### Post by bilbobagins on 2007-06-19
Hi not been able 2 get to computer,but had a go nearly there but ...jonathan@jonathan-desktop:~$ sudo fdisk -l

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19266   154754113+  83  Linux
/dev/sda2           19267       20023     6080602+   5  Extended
/dev/sda5           19267       20023     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux
jonathan@jonathan-desktop:~$ cat /etc/fstab
/dev/hda5 /storage ext3 defaults 0 0
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=72a78e4d-6a9e-470d-9c2d-9f2b81386595 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=7a0b082c-9422-4ca2-b888-e4a82d8356e9 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0    
# /dev/sdb1 525f782d-6ec8-42b6-85e1-78c6a9317967 /media/STORE ext3 nouser,noatime,auto,rw,dev,exec,suid 02

jonathan@jonathan-desktop:~$ 

the last line..sudo mount -a retutns storage does not exist, where clearly it does

 dev/hda5 /storage ext3 defaults 0 0
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=72a78e4d-6a9e-470d-9c2d-9f2b81386595 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=7a0b082c-9422-4ca2-b888-e4a82d8356e9 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0    
# /dev/sdb1 525f782d-6ec8-42b6-85e1-78c6a9317967 /media/STORE ext3 nouser,noatime,auto,rw,dev,exec,suid 02 
what needs fixing
                          hope to hear from you

---

### Post by dreadlord_chris on 2007-06-19
That last line:
```

# /dev/sdb1 525f782d-6ec8-42b6-85e1-78c6a9317967 /media/STORE ext3 nouser,noatime,auto,rw,dev,exec,suid 02

```
Should actually be 2 lines:
```

# /dev/sdb1 
UUID=525f782d-6ec8-42b6-85e1-78c6a9317967 /media/STORE ext3 defaults,noatime     0    2

```

the options *nouser,auto,rw,dev,exec,suid* are all implied by **defaults**

---

### Post by bilbobagins on 2007-06-29
Hi Chris.
Sorry not in touch sooner but had operation, but thats another story. followed your instructions now have the drive naned and mounted but still read only were have I slipped up? also tried to create home partition as per  Ubuntu Linux resources site and it dont work
9cant create logical partition in gparted on live cd) any sugestions. please. 
              Thanx Jon.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8f3ef320-d54e-4c98-b013-652b94e97f57 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=7a0b082c-9422-4ca2-b888-e4a82d8356e9 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
# /dev/sdb1
UUID=a114ef7b-699d-4da8-a6cd-209b3c61bf88 /media/STORE ext3 defaults,noatime     0    2

---

### Post by dreadlord_chris on 2007-07-02
> **bilbobagins said:**
> Hi Chris.
Sorry not in touch sooner but had operation, but thats another story. followed your instructions now have the drive naned and mounted but still read only were have I slipped up? also tried to create home partition as per  Ubuntu Linux resources site and it dont work
9cant create logical partition in gparted on live cd) any sugestions. please. 
              Thanx Jon.

been gone myself for a few days... hope your operation came out ok....
So, the drive mounts ok now - good... the *read-only* thing is just a minor annoyance: since this a a *storage* drive I'm assumming you probably want everyone to be able to read & write to it:
```

sudo chmod -R a+w /media/STORE

```

---

### Post by bilbobagins on 2007-07-02
Hi Chris, yea went ok, got it sorted in the end,one further question.
Ihave partitioned my 160GiB H/D to have a20GiBpartition for O/S and the rest for Files etc.which I`v done.. question is how do I automount it at the moment i have to mount the 140GiB  partition manualy ,any sugestions.
                                            Jon

---

### Post by dreadlord_chris on 2007-07-02
just go thru the same process that you did for the 250GB drive - make a mount folder in **/media**, use **fdisk** to find the */dev* point, and add it to your **fstab**

---

