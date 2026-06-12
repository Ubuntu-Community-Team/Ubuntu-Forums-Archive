---
title: "Issues with booting back into windows."
date: 2007-07-14
forum: General Help
---

### Post by drchaos619 on 2007-07-14
I have scoured the forums and from what I've read, those in my situation lost windows completely.

Before I begin, I'd like to state that I am a complete total noob when it comes to Linux. 

Prior to installing linux, I partitioned 30 gb for linux  in fat32. I installed Linux with little problem. I check the disk size when I enter ubuntu and I see 23.3 of 30 gb used, so I know its in the partition I allocated. 

My problem is that I can't get back Into windows at all. 

I'm hoping It has something to do with the MBR being messed up but before I do that, I'd like some input to make sure that I didn't accidentally erase my windows partition...which would be horrible at this point.

I installed GRUB and it doesn't recognize windows what so ever...another clue to my MBR theory. 

Now I'm not sure if I made the partitions wrong (i.e. boot and logical) and when I run HD checks, i get

hda (0,4) 
hda (0,0)

being a noob, I have no idea what that means outside of maybe recognizing two different partitions. 

but anyways, can someone either tell me or direct me to solutions or directions on what to do in plain ye olde english?

---

### Post by Ayuthia on 2007-07-14
First thing you can do is see if your Windows partition is still there.  You can do this by opening up a terminal and type:
sudo fdisk -l

---

### Post by drchaos619 on 2007-07-14
here is what I get. 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10768    86493928+  82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sda2           10769       14593    30724312+   f  W95 Ext'd (LBA)
/dev/sda5           10769       14593    30723808+  83  Linux

---

### Post by merlinus on 2007-07-14
When you got to the partitioning screen during install, do you remember what method you selected?

-merlin

---

### Post by drchaos619 on 2007-07-14
honestly, I don't remember. the trouble that I did have that I do remember during installation involved something along the lines of designating a partition with the symbol "/" to desgintate some sort of bootfile. other then that, I don't really remember.

is my windows partition gone?

---

### Post by merlinus on 2007-07-14
Judging by the output of:

sudo fdisk -l

it would appear so.

:(

/ is the root partition, where ubuntu is installed.  /swap should be small, no more than 1G.

From what I can see, /swap is in a primary partition (sda1), and / in a logical partition (sda5) within an extended one(sda2).

-merlin

---

### Post by Ayuthia on 2007-07-14
I could be completely wrong, but from what I see, you have created a swap partition under /dev/sda1 and it takes up space from 1-10768.  I thought that since you had Windows installed first, it would have already occupied the first portion of the disk.  The other part that I am confused about is that /dev/sda3 and /dev/sda4 are not there.  There is a possibility that Windows is there.

I have generally put my newer installs on the back end of the hard drive so what I said might be incorrect.

---

### Post by Ayuthia on 2007-07-14
Can you also post your /etc/fstab?  It would be interesting to see if /dev/sda3 or /dev/sda4 are there.

---

### Post by merlinus on 2007-07-14
FYI, ubuntu uses sda1-sda4 for primary partitions.  Logical partitions begin at sda5, even if there are no others.

So sda2 is an extended partition, and then the numbering begins with sda5.

-merlin

---

### Post by drchaos619 on 2007-07-14
Ayuthia:

I would be more then happy to If I knew the command to for the terminal. How does one go about doing this?

merlinus:

English please? lol

I appreciate all of your help. If there is any way that I can get back into windows, that'd be fantastic. You see, I'm a music producer and I have backed up all of the files on a networked server. Due to my past experiences....that I like to call jackassery.... I learned the hard way about backing up your files multiple times when you are pushing your hardware to its limit. Well, there Is one file in particular which never made it over which I would really love to have. I only backed up the last version of the file, and not the updated version unfortunatley. 

If my windows OS is gone, well that...in short...sucks. But if there is a way that perhaps some of my files still exist, is there a way to recover the individual file that I want?

---

### Post by merlinus on 2007-07-14
```

cat /etc/fstab

```

There are recovery cds that you might try.  Here is one:

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

Good luck!

-merlin

---

### Post by drchaos619 on 2007-07-14
thankyou merlinus....as requested, here is the fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=4a290f16-9c6f-4824-8761-64ee250b250f /               ext2    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=e4a1cd80-d08c-4593-bd7b-f73bbe880612 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0

i shall try the system recovery. is there anything else that i should fix about my system set up?

heh...its true. The more you know, the more you realize you don't know

---

### Post by Ayuthia on 2007-07-14
From what Merlin was saying, the information that I requested is not going to be found because of the way you created your partitions.  Right now, you have two "real" partitions--/dev/sda1 and /dev/sda2.  sda1 is your swap space and sda2 is the extended partition (an extended partition that is divided up into other logical partitions).  In your case, you only created one partition in sda2 and it is called /dev/sda5.  sda5 is taking up all the space in sda2.  If you take a look at your posted fdisk -l, you can see the start and end cylinders for each partition.  If you look at sda2 and sda5, they have the same numbers which means that sda5 occupies all the space of sda2.  

I am sure what I said made very little sense, but in short, he is saying that sda3 and sda4 will not be there because you did not create any.  If you wanted to see what is in /etc/fstab, all you have to do is type:
cat /etc/fstab.

---

### Post by merlinus on 2007-07-14
For sure, your install overwrote your windows partition.

Try the systemrescue cd -- perhaps you can still save some of your windows data.

-merlin

---

### Post by dagnabit dang doohickey on 2007-07-14
That is one manly swap partition.

This is a recovery tool that was posted by a forum mod in another thread today: [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec")
I've never used it but it looks interesting.

Whenever I've gotten a hard drive failure I usually find zen, but I'd rather just find my files.

---

### Post by drchaos619 on 2007-07-14
thankyou all for your help. i don't care if windows is gone. i can always reinstall it and do it right the  second time around. i just really would like to have that file. thanks again

---

