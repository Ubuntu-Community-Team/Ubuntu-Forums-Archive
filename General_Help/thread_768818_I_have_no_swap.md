---
title: "I have no swap?"
date: 2008-04-26
forum: General Help
---

### Post by oddworld on 2008-04-26
System monitor says I have 0b / 0b of swap. So I don't have swap?
I have 2 gigs of ram, do I need or want swap?
Why would I not have any?

---

### Post by tamoneya on 2008-04-26
although it may not be used on a regular basis it is still a good thing to have since if your computer crashes it will attempt to dump the ram onto the swap.  If you don't do this you have a lot more trouble figuring out what went wrong.  Run ```
sudo fdisk -l
``` and we can see exactly what is up with your partitions.

---

### Post by oddworld on 2008-04-26
```
davis@davis-desktop:~$ sudo fdisk -l
[sudo] password for davis: 

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24036   193069138+  83  Linux
/dev/sda2           24037       24792     6072570    5  Extended
/dev/sda5           24037       24792     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3c150c67

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       60801   488376000    f  W95 Ext'd (LBA)
/dev/sdb5               2       60801   488375968+   7  HPFS/NTFS

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2084e1fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       48641   390708801    7  HPFS/NTFS
davis@davis-desktop:~$ 

```

---

### Post by tvtech on 2008-04-26
you have swap /dev/sda5  look mom swap  

and yes you might want it it's like windows virtual memory paging file  good for hibernating as this is where it's your stored state is written too.  must be at least the size of available ram for this.

---

### Post by tamoneya on 2008-04-26
so you do have a swap space created(/dev/sda5).  It is probably not being automounted correctlyu in fstab.  Post the contents of /etc/fstab

---

### Post by tvtech on 2008-04-26
opps

---

### Post by oddworld on 2008-04-26
I copied fstab from a previous ubuntu
This is probably the problem - help me fix it.
Also: when I reboot I get error ata.00 {DDRY}  
I think this could be related to me copying fstab

```
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=14306992-88d4-4e02-a281-91b4d9204abf /               ext3    defaults,erro$
# /dev/sda7
UUID=221feec2-12cf-444a-9694-d1cfdb2fc6cb none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdc1       /media/400gb    auto    rw 0 0
/dev/sdb5       /media/video500 auto    rw 0 0






```

---

### Post by tamoneya on 2008-04-26
yep there is the problem.  Your previous install had /dev/sda7 as the swap partition.  Change it to /dev/sda5 and you should be all set.

---

### Post by oddworld on 2008-04-26
Thanks - Question: 
What is ```
UUID=14306992-88d4-4e02-a281-91b4d9204abf /
```
mean?

---

### Post by oddworld on 2008-04-26
it still says I have no swap:

```
  GNU nano 2.0.7              File: /etc/fstab                                  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=14306992-88d4-4e02-a281-91b4d9204abf /               ext3    defaults,erro$
# /dev/sda5
UUID=221feec2-12cf-444a-9694-d1cfdb2fc6cb none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdc1       /media/400gb    auto    rw 0 0
/dev/sdb5       /media/video500 auto    rw 0 0






```

---

### Post by the8thstar on 2008-04-26
Answer here: [http://en.wikipedia.org/wiki/UUID]("http://en.wikipedia.org/wiki/UUID")

---

### Post by tamoneya on 2008-04-26
UUID is the Universally Unique Identifier.  It helps to identify your harddrives.  They are helpful if you are swapping your harddrives around and /dev/sda1 swaps with /dev/sdb1. They are not necessary.  Just delete that line from the swap entry. it should look like this
```
/dev/sda5 none            swap    sw           $

```

Notice how /dev/sda5 is no longer commented out since now it is important since you no longer have the UUID to identify it.

---

### Post by oddworld on 2008-04-26
Ah thanks, now I have 6 gigs of swap
... oh the possibilities!

---

