---
title: "[SOLVED] Access to riad0 C drive"
date: 2008-04-13
forum: General Help
---

### Post by Gripp on 2008-04-13
seemed simple enough but I cant seem to find something appropriate for my case:

i have 2 drives in raid 0 - C: which houses my windows system
then i have my backup drive D: which is what i have wubi installed on

i have access to D: but not C.  i cant even seem to find any reminents of C

my raid was set up prior to installing any OS 

ls -l turns up nothing (likw, nothing...)
/dev/disk/bylabel only shows my main drive and external drive
and i dont remember/cant find the commands to list drives etc.

---

### Post by ago on 2008-04-13
If it is supported it will show up in /proc/partitions

---

### Post by Gripp on 2008-04-15
i dont see anything in any of the files in that directory...  that file itself is blank

i seem to recall somehow going into superuser mode to view some files last time i played with linux - but that was KDE and a while ago

but, then again, the properties show the file to be 0kb in size...

---

### Post by ago on 2008-04-16
cat /proc/partitions

---

### Post by Gripp on 2008-04-16
ago man you are great.  i've never seen someone so helpful on forums before :) 

   8     0  244198584 sda$
   8     1  488375968 sda1$   <-- looks like my winner
   8    16  244198584 sdb$
   8    32  244198584 sdc$
   8    33  244196001 sdc1$
   7     0   13671875 loop0$

i'm going to try to re-fgure out how to mount this over the weekend.  i'll let you know if i get stuck, but otherwise i'll spare your time.  thanks for everything!

---

### Post by Gripp on 2008-04-19
okay, i re-figured it, and this is what i get:

```
:~$ sudo mount -t ntfs /dev/sda1 /C_Drive
$MFT has invalid magic.
Failed to load $MFT: Input/output error
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

```

now, i did just run ckdsk on a windows boot, and rebooted twice, due to kernel panic of trying to kill init.......
it did find some errors, but no bad sectors and it fixed everything.  (but i think the errors were from the hard boot cuase by the crash that lead me to the kernel panic)

and, i'm also in Raid.. set up with intel raid drivers before the install of windows (so i'm not 100%, but i think that is a real raid)

i'll run chkdsk again, and reboot twice again
but if that doesn't fix it, then how to get around the loading dev/mappers stuff for my system to get raid working?

edit:okay, ran chkdsk again and had no errors. rebooted twice and got the same error when trying to mount that again.  started looking at dmraid.. seems like some tuff crap

---

### Post by Gripp on 2008-04-19
got it :D

installed dmraid  (apt-get install... method)
ran dmraid -ay
oddly this shows each disk as its won raid, kind of confusing.. just labeled them <nameOfDisk>1 2 3... 
then i tried mounting them

the first one said it was already mounted :confused:  but then the second did get my c drive mounted correctly 

now hopefully non of this messed with my windows install ;)

---

