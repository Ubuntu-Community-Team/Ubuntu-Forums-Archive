---
title: "Activating Swap During A Session"
date: 2007-05-09
forum: General Help
---

### Post by prdack on 2007-05-09
I all,
First thing first, when I'm using my PC after about 20 mins or so I get a system beep, I get a black screen displaying something like this message.
*Activating Swap...                         [ ok ]
*Checking root file system ... 
sck 1.39 (29-May-2006
dev/sda3: clean, 302388/12107776 files, 6377113124185857 blocks
                                                                 [ ok ]

*Checking file systems ... 
sck 1.39 (29-May-2006)

And then it shuts down, this happens everytime I use Ubuntu, any ideas?

Also when I boot up I only get a small blinking curser in the top left hand corner for about five mins and then the login screen. I have tried all sorts to sort this out but haven't mangaed to solve it yet.

You're help would be much appreciated.

---

### Post by Pox on 2007-05-09
The cursor in the top right flashing occurs when ubuntu does a full filesystem check... not sure what your problem is though. :(

---

### Post by owlhoot on 2007-05-10
> **prdack said:**
> I all,
First thing first, when I'm using my PC after about 20 mins or so I get a system beep, I get a black screen displaying something like this message.
*Activating Swap...                         [ ok ]
*Checking root file system ... 
sck 1.39 (29-May-2006
dev/sda3: clean, 302388/12107776 files, 6377113124185857 blocks
                                                                 [ ok ]

*Checking file systems ... 
sck 1.39 (29-May-2006)

And then it shuts down, this happens everytime I use Ubuntu, any ideas?

Also when I boot up I only get a small blinking curser in the top left hand corner for about five mins and then the login screen. I have tried all sorts to sort this out but haven't mangaed to solve it yet.

You're help would be much appreciated.

I had nearly the same problem, except mine happened on boot up. It could not create or access the swap file, and did a long file check before it finished loading. The same fsck 1.39 process started and then when finished it told me that my swap file could not be found. I need to find out how to solve this. Off to do some research. BTW, are you using edgy? Just curious.

---

### Post by prdack on 2007-05-12
> **owlhoot said:**
> I had nearly the same problem, except mine happened on boot up. It could not create or access the swap file, and did a long file check before it finished loading. The same fsck 1.39 process started and then when finished it told me that my swap file could not be found. I need to find out how to solve this. Off to do some research. BTW, are you using edgy? Just curious.

Hi,
Yeah I'm using edgy, tried installing fiesty but it gets to about 97% then just switches off. I have tried everything and just about to put my XP disc in my cd drawer if I can't solve the problem. Is there anybody that can help? I really don't want to go back to windows.

Thanks

---

### Post by mu2012 on 2007-05-14
I've been having basically the same problem on boot up since yesterday.  System hangs at "Checking file systems...fsck 1.39 (29-May-2006).  Running a dual-boot system with Win2000.  I have no problem logging into Windows.  Been using Edgy for a few months now with relatively few problems until yesterday.  Nothing new was added or changed, so I'm stumped.  I have no clue how to access my system.  Please help.

---

### Post by taurus on 2007-05-14
Can you boot your machine at all even to recovery mode from GRUB menu?  If not, do you have a LiveCD handy so you can boot from it and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by mu2012 on 2007-05-14
> **taurus said:**
> Can you boot your machine at all even to recovery mode from GRUB menu?  If not, do you have a LiveCD handy so you can boot from it and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

Thank you for your quick reply !!!   I was getting the same "Checking file systems"  message when booting in recovery mode as well.  

However, I just got back into the system another way !!!  After posting to this forum, out of desperation, I decided to do a Ctrl-Alt-Del and it worked...I'm back in !!!  Still no clue what's wrong with the system though, so I'm backing all my important data before I shut down and try to reboot to see if it boots up normally.  Either way, since I'll have all my data on backup, I'm considering  scrapping the entire installation and starting from scratch....I was planning on upgrading to Feisty soon anyway.  Thank you again and best regards !!!

---

### Post by mu2012 on 2007-05-14
Restarted the system and still having the same "Checking file systems..." issue.  

No problem getting back in doing another Ctrl-Alt-Del.  

Ran "sudo fdisk -l" and got the following output:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       50790    25598128+   c  W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/hda2           50793      153574    51801592+  83  Linux
Partition 2 does not end on cylinder boundary.
/dev/hda3          153574      155056      747022+   5  Extended
Partition 3 does not end on cylinder boundary.
/dev/hda5          153574      155056      746991   82  Linux swap / Solaris

Any suggestions as to what the problem can be ?  Thank you !

---

### Post by taurus on 2007-05-14
Can you also post your /etc/fstab?

```
cat /etc/fstab
```

---

### Post by mu2012 on 2007-05-14
> **taurus said:**
> Can you also post your /etc/fstab?

```
cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=67937fcf-fb9e-4b1c-91bc-64cce07566a3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=C43F-A29D  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=c25785e9-2617-4e80-a7a1-0d22245e2b1f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by prdack on 2007-05-15
Hi Guys,
We'll I think I have solved my problem, I ordered a live CD from Ubuntu which came yesterday, I installed it with no problems and everything seems to be running ok at the moment. I will keep you posted if anthing changes.

---

