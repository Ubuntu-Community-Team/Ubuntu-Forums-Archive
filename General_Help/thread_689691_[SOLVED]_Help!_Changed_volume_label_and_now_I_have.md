---
title: "[SOLVED] Help! Changed volume label and now I have problems."
date: 2008-02-06
forum: General Help
---

### Post by jorwex on 2008-02-06
Hey all,

I've been playing around with Ubuntu for 2 months now and I decided to reformat and install only what I now know I like. 

Some background info:
I've got a few partitions on one big 320GB disk:
-swap
-system
-extended
    -docs            (sda5)
    -storage        (sda6)

and the latter two are NTFS ones left over from windows. so I emptied space on the storage partition and created a new ext3 (sda7) at the end of it to slowly move files over to, and then slowly resize it, etc.

Well when I created it, somehow I didn't have permissions to write to it, so I used gksudo nautilus and changed the permissions tab of the properties window for sda7 to match what my storage and docs partitions had. then i was being stubborn and wanted the volume label to say something other than sda7 and used "e2label /dev/sda7 New" and then I got an additional folder in media called New in addition to the sda7 that was from before. Now my Gparted looks like this:

[IMG]http://glue.umd.edu/~jwexler/1.png[/IMG]

and when I boot, the splash gets half way through the progress meter and then i get this:

[IMG]http://glue.umd.edu/~jwexler/3.jpg[/IMG]

and I can't access sda5 or sda6. if i click on their folders in /dev/sda5/ and /dev/sda6/ they're empty!

when "Control+D" didn't work (as that screen instructs to continue the boot process), I freaked and then did Ctrl+Alt+Del and it magically booted. Every boot gets halted with that scary stuff. 

SO! i screwed up somehow. I'd rather just format again if it'll fix all of this, rather than mucking things up more. maybe it's a better idea to use this external harddrive I have to backup my storage drive onto, then format the storage drive to ext3 and copy it back. my external drive's a little iffy sometimes tho, and i thought this resizing method would be better. anywho

all i wanna know is, **IF i reformat, will I get access to those two partitions (sda5, sda6) back? or will that make me lose them forever?**

Thanks!

PS lemmi know if I can provide you with any extra info or logs, etc..

---

### Post by seventhc on 2008-02-06
when you created the new label, did you read the pop up box?? It basically...creating a new label on an existing partition will erase all data on /dev/hda. I think setting the disk labekl is something you would do when creating new partitions, not for pre-existing ones. If you have the info backed up, the only thing I can think of is maybe deleting and re-creating them. I only see a small portion where there is data, everything else looks empty to me. If this was a new install, I personally would just re-install again. I wouldn't want a fresh install startin g with any problems.
Wait for more options though as maybe someone here knows more, or has a better suggestion.

...they arent lost forever, but perhaps the data on them is...

---

### Post by jorwex on 2008-02-06
> **seventhc said:**
> creating a new label on an existing partition will erase all data on /dev/hda..

i dont have something called /dev/hda

what are you referring to? 

The two NTFS partitions were called "Storage" and "My Docs" and I made those labels in Windows XP, and they always appeared on the Desktop in Ubuntu.

But those names never appeared under the Label column in Gparted. That confused me a bit. 

What i did was, unmounted the new ext3 filesystem on the end there, formatted it again to ext3 to see if it would prompt me for a disklabel, and it never did. so while it was still unmounted, i changed the disklabel with that command i pasted in my last post.

so I never added the disklabel on the existing partition in question (sda7).

so from what you're saying, shouldn't my sda5 (docs) and sda6 (storage) still be there? i never touched those partitions. how do i get them back?

---

### Post by jorwex on 2008-02-06
```
Log of fsck -C -R -A -a 
Wed Feb  6 17:16:27 2008

fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Unable to resolve 'UUID=3486e709-f66d-4319-8489-5ee27ce77792'

fsck died with exit status 8

Wed Feb  6 17:16:27 2008
----------------
```

here's a log, if that's usefull

---

### Post by seventhc on 2008-02-06
from that pic you posted, sda6 looks empty to me. It's all white, no yellowish color indicating data.
both 5 and 6 show as having no space used, and the triangle boxes next to them.
I personally think there is no data on them, I would probably reformat them. Is this a dual boot? if not why use NTFS?

---

### Post by jorwex on 2008-02-06
that's not because its "empty." it's because GParted cannot read the filesystem:

[IMG]http://glue.umd.edu/~jwexler/blah.png[/IMG]

i need to run some sort of repair i think. i used this program once for a friend and it worked well. im not sure if that's quite what i need...

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

i appreciate the help. please forgive any apparent negative tone i have--i dont mean it. i just want my crap back!

thanks,

jordan

---

### Post by plucky on 2008-02-06
jorwex,

When the boot fails try **enter** then a **ctrl D** to see if it continues to the login screen.

If it does then login and open a terminal and type ```
blkid
``` and ```
cat /etc/fstab
``` and post result.I think the UUID of one of your partitions has changed and The UUID in Fstab is incorrect.

Good luck

---

### Post by jorwex on 2008-02-06
okay here's what i got. 

Ctrl+D did in fact do nothing. I put those two commands and got this:

[IMG]http://glue.umd.edu/~jwexler/00005.jpg[/IMG]
[IMG]http://glue.umd.edu/~jwexler/00008.jpg[/IMG]

I did control+alt+delete like before and got back into ubuntu, and ran the commands in a terminal to see if they matched (so I could just copy and paste the info instead of typing it all manually). a quick glance shows that they're the same (i think)...

```
jorwex@jorwex-desktop:~$ sudo blkid
[sudo] password for jorwex:
/dev/sda1: TYPE="swap" UUID="c45bf21f-918a-49fe-b327-96a1815975c0" 
/dev/sda2: UUID="3ec513e5-3f56-4e41-a279-152f57571aca" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="AA6073066072D911" LABEL="My Docs" TYPE="ntfs" 
/dev/sda6: UUID="8E6C99096C98ED69" LABEL="Storage" TYPE="ntfs" 
/dev/sda7: UUID="dd6fe16d-a90e-4a8b-ae7d-ccb6f1fd21ec" SEC_TYPE="ext2" TYPE="ext3" LABEL="New" 

```

```
jorwex@jorwex-desktop:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=3ec513e5-3f56-4e41-a279-152f57571aca /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=AA6073066072D911 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=8E6C99096C98ED69 /media/sda6     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=3486e709-f66d-4319-8489-5ee27ce77792 /media/sda7     ext3    defaults        0       2
# /dev/sda1
UUID=c45bf21f-918a-49fe-b327-96a1815975c0 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

does that help? thanks for the help so far!

---

### Post by plucky on 2008-02-07
Output from **blkid**
[color=red]/dev/sda7: UUID="dd6fe16d-a90e-4a8b-ae7d-ccb6f1fd21ec" SEC_TYPE="ext2" TYPE="ext3" LABEL="New"[/color]
and output from **cat /etc/fstab**
[color=blue]# /dev/sda7
UUID=3486e709-f66d-4319-8489-5ee27ce77792 /media/sda7     ext3    defaults        0       2[/color]

have different **UUID's**
You need to ```
gksudo gedit /etc/fstab
``` and copy and paste the **UUID** from the BLKID output and replace the UUID in the Fstab file. Then your system should boot correctly.

Good luck.

---

### Post by jorwex on 2008-02-07
awesome! it's all working now! you are a godsend.

one quick question tho. why in Gparted does it not show the labels in the Label column for my Storage (sda6) and My Docs (sda5) partitions, but it does for the New (sda7) partition that I created---however ALL three are displayed correctly on my desktop.

is that indicative of something still wrong? thanks

[IMG]http://glue.umd.edu/~jwexler/Screenshot-2.png[/IMG]

---

### Post by plucky on 2008-02-07
Not really sure,it might be that they are NTFS.
Please mark thread as solved using thread tools at top of page.

Thanks.

---

### Post by jorwex on 2008-02-07
I thought this was deviating too far from the original topic so I made a new one here that's more to the point...

[http://ubuntuforums.org/showthread.php?p=4288217#post4288217](http://ubuntuforums.org/showthread.php?p=4288217#post4288217)

---

### Post by jorwex on 2008-02-07
thanks! i didnt know how to "SOLVE" threads before that.

---

### Post by seventhc on 2008-02-07
I am glad you showed up plucky, as you were able to solve it and teach me something in the process. :) you'll get a thank you from me. :)

---

### Post by jorwex on 2008-02-09
I'm very new to this whole linux thing, but after this problem has happened for a second time, does that merit submitting a bug report for gparted?

i was running it from a gparted lve cd this time, and deleted and then added some space to a partition, and then ran into the same problem. 

is there some way that the fstab file in ubuntu is supposed to be fixed for you? or is it expected that you have to fix it yourself?

---

