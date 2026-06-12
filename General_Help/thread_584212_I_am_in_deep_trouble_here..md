---
title: "I am in deep trouble here."
date: 2007-10-20
forum: General Help
---

### Post by thesavge on 2007-10-20
I tried installing Ubuntu 7.1 today to dual boot with Windows XP. I am a complete linux noob, I will just put that out there right now. I tried partitioning as I wanted, and something went very wrong. Now, my computer thinks that i have a 5 gig hard drive, not a 120 gig one. i can no longer access the other partition, as the computer cannot find it. I can't even use the XP rescue cd, because it doesn't see Windows present in this 10 gig ubuntu partition. How can I get this computer to dual boot without losing any information from the windows partition?

---

### Post by chillman88 on 2007-10-20
That sounds really weird, i have absolutely no clue. You did resize the windows partition using manual partitioning, instead of "use entire disk guided" right?

---

### Post by thesavge on 2007-10-20
unfortunately, i had my brother assist me, who thought that the guided one was going to reformat the entire disk. because of this, he did the manual. he is rather experienced, but even he doesn't know what went wrong. i think he may have deleted the windows partition. i know he created the new ones at the end of the disk though, Does this mean all the information is on the drive, but i just cant get to it now?

---

### Post by spikeyone on 2007-10-20
:(

If your XP partition survived, Ubuntu would be able to see it... I think you might have wiped your XP partition.

Can you open a terminal and enter the command:

cat /etc/fstab

and tell us the output?

---

### Post by chillman88 on 2007-10-20
yes, even if the partition is deleted the data is still there

If you lost your partition, x.x you will have to buy software to resotre it

try running cfdisk and see if it displays a windows partition, let me know

---

### Post by thesavge on 2007-10-20
result of fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=c779495c-8909-47e8-b06d-f204cd1d5aaf /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=b2b9f7a5-fae5-4fbb-b2db-44cbdfdddb41 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
matt@none:~$

---

### Post by thesavge on 2007-10-20
i'm not sure how to run cfdisk, and i don't want to mess anything up further. so, id like to ask: what command should i put into the terminal?

---

### Post by chillman88 on 2007-10-20
either cfdisk, or cat /ect/fstab

the first will display what partitions are on your hard drive, the second will list what ubuntu has detected

---

### Post by thesavge on 2007-10-20
cfdisk has a fatal error and will not run.

---

### Post by chillman88 on 2007-10-20
hmm... weird post the output of cat /etc/fstab then please

---

### Post by thesavge on 2007-10-20
this is the result of the cat /etc/fstab


# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda5
UUID=c779495c-8909-47e8-b06d-f204cd1d5aaf / ext3 defaults,errors=remount-ro 0 1
# /dev/sda6
UUID=b2b9f7a5-fae5-4fbb-b2db-44cbdfdddb41 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
matt@none:~$

---

### Post by spikeyone on 2007-10-20
Wow, your fstab is kind of weird. It shows partitions 5 and 6 but not 1-4. Maybe windows still is in there somewhere...

When you turn on your computer and it shows the GRUB menu, Windows isn't there?

When you click on "Places" on the menu bar and then "Computer," does it possibly list your partition there? Maybe it isn't mounted.

---

### Post by p_quarles on 2007-10-20
That output doesn't look very good, unfortunately.

Try running:
```
sudo fdisk -l
```
and post the output here.

---

### Post by Taino on 2007-10-20
> **thesavge said:**
> cfdisk has a fatal error and will not run.

Just a quick note on cfdisk...

Try...

sudo cfdisk

It may ask for your password, enter it and it'll display your partition info and let you edit your partitions.

---

### Post by CouchMaster on 2007-10-20
Or maybe run fdisk -l and post the results...

---

### Post by thesavge on 2007-10-20
here is sudo fdisk:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd5abd5ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       13741       14593     6851722+   5  Extended
/dev/sda5           13865       14593     5855692+  83  Linux
/dev/sda6           13742       13863      979933+  82  Linux swap / Solaris

Partition table entries are not in disk order

and sudo cfdisk told me the logical partitions overlap, so it didnt work.

---

### Post by chillman88 on 2007-10-20
Umm.. yeah, if you have absolutely necissary data on that windows partition, you better look into partition restoration software, idk if there is any free though? Correct me if i'm wrong, but it looks like you lost your windows partition x.x

---

### Post by thesavge on 2007-10-20
i attempting to use testdisk right now to try and fix the problem. it is analyzing the disk right now, and it DOES see autoexec etc. and all the other windows files, including my personal documents.

---

### Post by chillman88 on 2007-10-20
That's a start, good luck!

---

### Post by thesavge on 2007-10-20
yeah, i'm hoping all goes well as well. i was hoping that i could fix it from without using a text based program like that, (i'm a bit young for experience with much else than a nice, polished GUI. our first computer ran windows 3.1) if something goes really wrong, i'll make sure you guys hear about it.

---

### Post by p_quarles on 2007-10-20
It looks like you somehow managed to turn the entire hard disk into an extended partition. As you're seeing, it didn't overwrite the Windows data, but it did make it unrecognizable to the bootloader. Hopefullly you will be able to get it back to an NTFS partition without losing data.

Anyway, next time you try to install, either use the "guided -- resize current partition" option, or *make sure* that create new partitions for the root filesystem and for the extended partition.

---

