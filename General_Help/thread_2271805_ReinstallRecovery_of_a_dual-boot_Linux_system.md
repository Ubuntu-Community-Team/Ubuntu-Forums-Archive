---
title: "Reinstall/Recovery of a dual-boot Linux system"
date: 2015-04-01
forum: General Help
---

### Post by pmi2 on 2015-04-01
I have had a dual-boot system for a couple months, including Ubuntu 14.04LTS as the first installed OS, and various other linux versions or distros as the second.  Separate partitions, separate home directories pretty much installed in default locations, and shared Data and Archive partitions.

I am wondering if it is possible to back up and restore an individual partition including the os and home directory in one pass?  

By this I mean NOT by creating a complete disk image which takes up as much space as the original partition, or by reinstalling the os and resoring Home.  

I have tried doing this using Clonezilla from a live CD, but I was not completely successful.  The restored os booted, but with errors, and in "Software Rendering Mode".  It was obviously not an exact restore.

I believe I have done this same kind of partition backup/resore in the past successfully using Windows 7 as the first and Linux as the second (or 3rd) installed os, but I am not sure I ever tried with multiple Linux installations.

Basically what prompted me to ask the q were some posts in this thread:

[http://ubuntuforums.org/showthread.php?t=2271778](http://ubuntuforums.org/showthread.php?t=2271778)

describing essentially what I have been trying to do... :D

---

### Post by bardo2 on 2015-04-02
I am not sure if i understand your q:

are you looking for a backup? OR do you want to use some data from different OS installations without the need to move it around?
Are you comfortable with OS boot procedures? AND did you understand the UID problem mentioned in above thread?

Please be a little more elaborate on what you really want, what you are able to do on your own, and what gap do we need filling?

> **pmi2 said:**
> I am wondering if it is possible to back up and restore an individual partition including the os and home directory in one pass?  


Yes, of course. Do you have enough disk space handy for it?
would you give some info on your current partitoning - like commented output of ```
lsblk
```

---

### Post by pmi2 on 2015-04-02
> **bardo2 said:**
> are you looking for a backup?No, but I am not attached to Clonezilla in any way, and if there is a better option, I will switch to that. (on systems that had Windows as the first installed os, I have used Acronis TI in the past)

> **bardo2 said:**
> Are you comfortable with OS boot procedures? AND did you understand the UID problem mentioned in above thread?Yes, for the most part, although with UEFI (which is disabled on this mobo) not so much.  I admit I did not read that in all detail, because it seemed familiar, and described what I had done in the past, and wanted to repeat now.

> **bardo2 said:**
> Yes, of course. Do you have enough disk space handy for it?
would you give some info on your current partitoning - like commented output of ```
lsblk
```Yes, I set the partition to be identical in size b/f I started the restore.  I did make some changes afterwards, but it is basically this:

```
peter@Flattop:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 232.9G  0 disk 
&#9500;&#9472;sda1   8:1    0  56.3G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9500;&#9472;sda3   8:3    0   7.9G  0 part [SWAP]
&#9500;&#9472;sda4   8:4    0  56.3G  0 part 
&#9492;&#9472;sda5   8:5    0  56.3G  0 part 
sdb      8:16   0 465.8G  0 disk 
&#9492;&#9472;sdb1   8:17   0 232.9G  0 part /media/peter/Archive
sr0     11:0    1  1024M  0 rom 
```

sda1 and sda5 are my two os partitions, sda5 was the one I attempted to restore. sda2 is an extended partition, which has about 56G left (unallocated) left after sda5 is installed.  sda4 is the shared Data partition. sdb1 is my archive, on a separate disk drive.  I have around 2x as much disk space as required, sda2 is about 112 Gb, of which 56Gb is used by sda5.

The setup is similar to what I have used in the past, with the exception that there are two Linux os partitions, as opposed to one Windows and one Linux.

edit:

Basically, I would like to be able to back up a Linux os partition (not a whole disk, not just the home directory), in something smaller than a sector-by-sector disk image, and restore is later, in one operation.

---

### Post by bardo2 on 2015-04-03
Hey, excellent! - You seem to be doing fine in general with what you are doing.

I had no intention to point you to a "click here and there"-solution, because on my own machine, i am doing most things manually from the commandline (while writing them down - or using history afterwards), and with time and experience - keep those experiences as bash scripts - to be used as a reference or converted into a command later. Thereby i did create a couple of backup/restore scripts over time and i am quite familiar with everything, that is necessary. And - just to be clear: most of the work is usually done in one line only, the rest being preparation, checking, housekeeping,...

Still, i would appreciate you being more clear about what you are trying to do. I am going to introduce words in the form of questions:
[LIST]
[*]Do you want to be able to actually boot up from your backup (which would require some more work)?
[*]Are you interested to access your backup from any OS partition frequently (which would be more difficult, if compression were to be used)?
[*]Are you happy to keep just the one backup (from the time, when it was created) or are you into versionning it (like keeping serveral versions to be able to "go back in time")?
[/LIST]
At first, i thought, you were interested to backup your system including some mounted partitions - in one go - without wasting space by doubling the unused space in the process.
Looking at your partition sizes, i guess you want to backup to your archive, and i assume you want to backup just the "/" partition with everything it contains. (On my systems, / partitions used to be much smaller, although i never separate /home either, because i rely on data to be stored in a separated /mnt/data partition.) thus i am wondering about how much unused space you may have in yours.

Finally: are you aware of (or already using) tools like rsync or rdiff-backup?
As you seem to be working locally on one machine only, you might be interested to know: even disk images can be made in such a way, that they do NOT contain empty space, but it would be more difficult to restore a single file from a compressed disk image, because to the OS, it would just be a giant blob of data.

So, am i on the way to understand, what you want at all?

---

### Post by pmi2 on 2015-04-03
> **bardo2 said:**
> So, am i on the way to understand, what you want at all?Yes, I think so.  

> **bardo2 said:**
> Do you want to be able to actually boot up from your backup (which would require some more work)?I want to be able to restore the complete backup to a new or wiped partition, and then boot the os from that partition.

> **bardo2 said:**
> Are you interested to access your backup from any OS partition frequently (which would be more difficult, if compression were to be used)?Not necessy.  I have separate tar archives to access user/data files if needed.  I usually have backups of the complete os separate from user files that can change daily. 

> **bardo2 said:**
> Are you happy to keep just the one backup (from the time, when it was created) or are you into versionning it (like keeping serveral versions to be able to "go back in time")?I usually have multiple backups, on disk, and some form of compression is helpful.

Acronis True Image did a good job, at least before the 2015 version which seems to have split some functionality, but it only works if your primary os is Windows.  

> **bardo2 said:**
> Looking at your partition sizes, i guess you want to backup to your archive, and i assume you want to backup just the "/" partition with everything it contains. (On my systems, / partitions used to be much smaller, although i never separate /home either, because i rely on data to be stored in a separated /mnt/data partition.) thus i am wondering about how much unused space you may have in yours.Yes, I back up to a separate disk drive, internal or external, in case of drive failure.  (Especially with this system, because I assembled it from used parts, so component failure is to be expected.)

It is a dual-boot system, so I want to back up (and restore) either of the two partitions, independently of each other.  There are two os partitions, a Data partition, some unallocated space, and an Archive partition on a separate disk.  Not all were mounted when I ran lsblk before, here it is again:

peter@Flattop:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 232.9G  0 disk 
&#9500;&#9472;sda1   8:1    0  56.3G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9500;&#9472;sda3   8:3    0   7.9G  0 part [SWAP]
&#9500;&#9472;sda4   8:4    0  56.3G  0 part /media/peter/Data
&#9492;&#9472;sda5   8:5    0  56.3G  0 part /media/peter/Mint
sdb      8:16   0 465.8G  0 disk 
&#9492;&#9472;sdb1   8:17   0 232.9G  0 part /media/peter/Archive
sr0     11:0    1  1024M  0 rom  


The os partitions(/ and Mint) are actually bigger than needed.  "/" is 62% unused, I use the home directory for some personal files and testing.  "Mint" is 75% unused. The bulk of my personal files are in the "Data" partition.

> **bardo2 said:**
> Finally: are you aware of (or already using) tools like rsync or rdiff-backup?Aware, yes, but not using them at this time.  My scripting skills are limited and I have not written any recently, just modified a few I came across.

> **bardo2 said:**
> As you seem to be working locally on one machine only, you might be interested to know: even disk images can be made in such a way, that they do NOT contain empty space, but it would be more difficult to restore a single file from a compressed disk image, because to the OS, it would just be a giant blob of data.I believe Acronis and other Windows backup software does that, but I have not come across it in Linux (not yet, anyway).

---

### Post by bardo2 on 2015-04-03
Thank you for being patient enough to write this long reply.

And this time, i got an idea - or two - of what you want and may need. :-)

Well, several things to learn:

A disk consists of more than just a bunch of partitions (like partition table, boot loader, for example). Therefore you need or a complete disk image or a partition image + some more stuff in order to restore a working system onto a different disk. And because disk sizes usually arent EXACTLY the same, there is even more to it. In other words, to enable a complete failover for a dying disk is rather complicated. I myself went for a setup, that is independent of a failing disk (at least) by using some raid with 6 drives, 2 of them just for redundancy. But still, i have backups!!!

Partition/disk backups in their raw form take up as much space as the partition itself would. But there are several measures, that can yield such a backup worthwhile. (1 extreme example: i have an old pc with a 500 GB drive in it running some tricky configuration (hand-made kernel with ubuntu-trusty-32 on top of it). That configuration is valuable and precious to me, it took a lot of time to get it to work. So i wanted a backup (to another machine). I decided to go for a total image of the drive (a.k.a. 500 GB), but... after investigating some useful techniques, i am down to 3.7 GB backup space for the entire thing!).

All in all, i consider the idea you are counting on to by rather (and maybe too) complicated.

Since you do not absolutely need to access single files, and because you seem to be familiar with partition backups, i suggest sticking with those. (Will come back to this topic shortly)

Scripting doesnt stand out as your forte. So we'll try to keep it as simple as possible.

Ok, now to the path i am suggesting:
Basically, you can fetch the raw data from a drive with sudo dd ....
dd can output to stdout, where it could be compressed before it gets send out to the net (in your case: stored onto another filesystem) with any compressor. i used bzip2
for the compression to be effective, it makes sense to clear the unused space beforehand (zero it out). Several techniques are available. the easiest would be "zerofree".
Only linux partitions can be prepared this way. Windows needs another program to run from inside windows: SDelete
And finally: the swap partition can be cleared too: just needs to keep the UUID and formatting in place. (howto not included here)
Beware: zerofree shall not be run from a mounted partition, so you will have to run it from recovery mode, or from a live ISO.
All those preparations have to be executed each time you want to backup and compress the disk image in a space-efficient manner.
And once you are done with those, an easy "dd {arguments} | bzip2 > out.filename" would do the trick.

Anything unclear so far? ;-)

---

### Post by pmi2 on 2015-04-03
No, not unclear, but just to be clear at my end, I don't need the entire disk, just an individual os partition.

edit:

Raid is not in my future, at least not on this machine.  I have run Raid 1 mirrors as well as striped sets in the past for other reasons, but it seems overly complicated for this.

---

### Post by bardo2 on 2015-04-03
> **pmi2 said:**
> No, not unclear, but just to be clear at my end, I don't need the entire disk, just an individual os partition.
Ok, that makes it somewhat easier. If you use a partition image, you may compress it (after zeroing unused parts, see above). But, since you intend to restore (in case of an emergency/replacement) onto another drive with possible slightly different partition size, a disk image would leave you with the task to recover from size differences (as well as setting up boot and the partition table) manually later. - That is possible, but why use that format in the first place, when you already know, you are not going to restore to the same partition anyway?

I would - in such a case - go for saving the files only, of course with compression, thus allowing to restore onto a different filesystem/partition with ease later. In that case, a nice and handy tool would be "tar" (commandline) which does preserve permissions and such (if executed with sudo), and can compress in one go.
> **pmi2 said:**
> edit:

Raid is not in my future, at least not on this machine.  I have run Raid 1 mirrors as well as striped sets in the past for other reasons, but it seems overly complicated for this.
No objections there. raid, especially the standard stuff, is quite complicated and cumbersome.

edit: ah, if you use UUID in fstab, as most users do, you will have to set those later during partition formatting, or - somewhat easier - change fstab after the restore. No big deal, and even tiny, since setting up partitioning and bootloader is way more challenging. :-)

edit2:
The main disadvantage of all those ideas would be the lack of redundancy. We all know, that a bit flip could render a compressed file worthless. If it is a compressed tar archive (*.tar.bz2), then a lot of files would be at risk. One can get some redundancy by manually adding error correction codes, there is a tool around, that can do that. see [https://en.wikipedia.org/wiki/Parchive#Linux]("https://en.wikipedia.org/wiki/Parchive#Linux")

---

### Post by pmi2 on 2015-04-03
Well, I am already familiar with tar and compressed tar archives (one of the few things I can actually say I am familiar with).  I don't think it is an efficient way to back up a whole os partition.

I do use UUIDs in fstab, although it is a really simple fstab, the only line I had to add for the above system was for the Archive volume.

The problem which led to this thread was overcome by first doing a fresh install, and then a restore over that  from the backed up image.  That worked, but everything else I tried gave me errors. Note that I had to make the new partition identical in size for this to work.

I think we are coming around to the answer that what I want can be done, but not in one pass.

How do you plan on recovering your customized os that you mentioned a couple posts earlier?

---

### Post by bardo2 on 2015-04-03
As i have the whole sda.img (originated from dd) in compressed form on the backup server, i just booted the machine from a live-ISO, conncted the network and read from there into bunzip2 directly to sda. That worked fine. net + unzip was fast, writing the 500 GB took a while. :-)

---

### Post by pmi2 on 2015-04-04
I don't think I ever tried dd on a complete partition, or a complete drive.  
Can you post an example of the command, so I can try it on a partition?  It should be fairly quick in my case, since I only have 60Gb.

---

### Post by bardo2 on 2015-04-04
just the one most important line from the script:
```

# create the image like so:
sudo dd if=/dev/sda | bzip2 > sda.img.bz2

# restore from image like so:
bzcat sda.img.bz2 | sudo dd of=/dev/sda

```

---

### Post by pmi2 on 2015-04-04
Looks promising so far, although I have not had a chance to go through a complete backup/restore cycle, I will try it later today. Thanks!

---

### Post by bardo2 on 2015-04-04
just for clarity: you are NOT doing that from the running OS, but from a live ISO, right?

---

### Post by sudodus on 2015-04-04
This thread is a great teaching and  learning experience :KS I think it will be useful for many other people at our Ubuntu Forums.

It is rather similar to how I learned to make images, that can be restored into the same and other computers. ***dd*** is nick-named 'disk destroyer' because it does what you tell it to do, which is not always what you intend to do ;-) dd is *very* powerful and useful, but double check and triple check before pressing the Enter key!

-o-

Gradually I have found other tools, that I find more efficient for many cloning, imaging and backup tasks, but I still use dd too. You wrote in the first post that you tried ***Clonezilla***, but without success. I still run it in ***'beginner mode'*** most of the time, and I use it to make a ***full image*** of a drive. This way it is much easier than what you tried to do, and much more likely to create images, that can be restored to fully working systems. After learning and getting confident with Clonezilla, I prefer it to dd. It is faster and safer. You need not zeroise the unused drive space. You need not copy unused blocks. It keeps track of bootloaders and special data areas near the heads of the partitions, so restoring is quite automatic. And it asks questions - helps you double check - before starting the process.

Small systems, for example your testing systems, can easily be backed up as ***tarballs***, either completely manually as described by bardo2, or with the ***One Button Installer***, which can also [re-]install the system or port the system from the tarball to another computer. The One Button Installer can also manage the bootloader and what is needed for the system to work, but only in BIOS/CSM mode, not in UEFI mode.

Images made with dd and Clonezilla need target drives of the same or larger size compared to the source drive. Backup or porting a system with a tarball needs a target drive, that is big enough to expand the files, but it does not bother with the unused space, so the target drive can be smaller than the source drive. The same holds for a backup with rsync.

-o-

I'm writing this in order to inspire for the future. I think it is a  good idea to continue your current work with dd and bzip2, but later on, you might feel  like trying something more efficient. Finally, remember that you can only really rely on a backup, that you have tested. In other words, I suggest that you get a third HDD and test that it works, when you restore the system from the image in the second drive into that third drive.

---

### Post by bardo2 on 2015-04-04
@sudodus: Hey, thank you for your encouraging words! As i am pretty new to these forums, i appreciate those very much.

Ok, thx for suggesting clonezilla. I am going to take a look at it. Only for me personally, it is not necessary at all (i am a ZFS user), and because of my lack of experience with it, i had no grounds to recommend it. I am aware, that my knowledge is limited, especially compared to the dev of OBI :-)

And my style of communication is challenging - to say the least - i guess to both parties. And it is difficult to do that without a clear "contract", without being clear about how responsabilities are being distributed. Anyway... i looked it up, i seem to be in a somewhat similar life situation to yours... just wasting my time in here, trying to pass on, what has been passed on to me before.

I invite you to take over from here, if you stick to one of the "easier, faster,..." solutions, i am not familiar with. you are welcome!
And, btw: happy easter bunnies! ;-)

---

### Post by pmi2 on 2015-04-04
> **bardo2 said:**
> just for clarity: you are NOT doing that from the running OS, but from a live ISO, right?From a different Linux partition, where I installed zerofree and some other tools.  Ultimately, I would be doing this from Live DVD, or more likely, a USB thumb drive.

I should have been more clear in the beginning, sorry:  This is intended for a dual-boot, Linux/Linux system, so there would always be a working os in the first partition, listed as /dev/sda1 above, and the os being backed up and restored would be on a different and separate un-mounted partition, for example above /dev/sda5 or dev/sda<x>.

If by your q you mean do I know what I am doing, then no, not all the time, but if I did, then I probably would not have needed your help... :D

> **sudodus said:**
> ...dd is nick-named 'disk destroyer'...I actually have a separate disk image of both working partitions, as well as tar archives of my personal files, offline for the purpose of this test.  Am I double-checking everything enough? Based on past experience, probably not, therefore the multiple backups ;)  

I have used dd before, but not for this purpose, probably because there were other alternatives at the time.

I am familiar with Clonezilla, it was the first thing I tried to use here, works fine on the complete disk, have used it in the past, but for some reason it did not work in this instance.  At least not in this sense: the restored partition image booted, but with errors.  (File system seemed to be there, my home directory compared ok)

UEFI is disabled on this system since before Linux was installed.

If this does not work, then I will try the tarball next.

edit:

Oh yes, Happy Easter!

---

### Post by sudodus on 2015-04-04
@bardo2,
It is not my intention to take over this thread. I think you are doing an excellent job. It is a good idea to start with a simple, yet powerful tool.

@pmi2,
When you know the method with dd and bzip2, and you have good backups, and you have time, you might try some other backup/cloning/imaging tools.

Good luck and happy easter to both of you :-)

---

### Post by bardo2 on 2015-04-04
Ok, yeah, i remember the thread title saying something about dual-boot...
and yes, you seem to be approaching your system just as i do mine (to have a second system at hand is very convenient in many cases). So yes again, no ISO needed, as long as the partition getting zerofree/dd/backup is not mounted at that time. Sorry, that slipped out of my view for a moment (short attention span at times).

While you are proceeding towards your safety-net solution: from my use of ZFS i learned, that if you are thinking long-term, you are going to see drives with 512 byte sector size dying in favor of the AF (advanced format = 1 sector = 4k) drives. That introduces another argument against disk images, because it may be increasingly difficult to restore those onto a drive with a different physical geometry. But as long as your replacement drive still has the old geometry, there is no problem. And once that changes, there is a path available to loop mount the image and extract files via rsync onto the new drive. So no problem yet.

Still preoccupied with "future-proof": you may see drives larger than 2 TB soon, that the old partitioning format (MBR = master boot record) would not be able to address. I moved towards gpt-partitioning years ago and you will have to plan accordingly, if you switch to it someday. For now, let me just leave the note in here in case other readers may take your solution for granted without considering such issues.

Finally: yes, a good backup must have a verified strategy to restore from it, and you are going to test that sooner or later. At least "in principle" i gave you commands, that did the job on my own machine (the older one), so i am confident, that apart from possible disk failures or missing redundancy you will be fine.

Still, once you got the job done, i would be pleased to get an update, maybe even a [solved] for the thread. :-)

---

### Post by pmi2 on 2015-04-05
Well, this IS an "older" machine, or rather a collection of old parts, so I am safe for now, ;)

I will post the results as soon as I run the test on the actual second os partition, for now I have just been trying your directions on a small dummy partition I created temporarily.  

dd from one disk with bzip2 into a file on a second disk seems to take a long time.  I think the last shorter test came out to 8Mb/sec, so a 60Gb partition will take a while.  bzip2 may produce a smaller image file so you don't have to write as many bytes, but we can't avoid reading the entire partition, or writing the entire partition on restore.  By comparison, Clonezilla does not have to read empty disk space when it makes a partition image, so it will always be faster.

Not sure I have enough time tomorrow, but by Monday evening I will have some results.

---

### Post by bardo2 on 2015-04-05
> **pmi2 said:**
> dd from one disk with bzip2 into a file on a second disk seems to take a long time.  I think the last shorter test came out to 8Mb/sec, so a 60Gb partition will take a while.  bzip2 may produce a smaller image file so you don't have to write as many bytes, but we can't avoid reading the entire partition, or writing the entire partition on restore.  By comparison, Clonezilla does not have to read empty disk space when it makes a partition image, so it will always be faster. 

Absolutely! In a way, using dd is very crude, we did not yet think about possible read errors and their consequences...
BTW: In the meantime, i had a glance at clonezilla, and guess what? It doesnt support zfs - to begin with. And while i made a clone of a whole disk, it duplicated the drive partitions UUID's, but failed to recreate the swap partition properly. (both are problems, that would have to be dealt with.) So i am shutting down playing with this tool for good. It may have its use-cases, but none for me.

---

### Post by pmi2 on 2015-04-06
It looks like this approach works well, at least for my purposes, :)

This means for backing up and restoring one of several Linux os partitions, with compression, and without having to boot from a live CD or USB drive.  Backup and restore can be automated using a  script.

I had to shrink the partition to be able to run multiple tests and compare results in one evening, so I am testing with a 16GB partition which has  about 50% free space.

I used the following example[quote=bardo2]
# create the image like so:
sudo dd if=/dev/sda | bzip2 > sda.img.bz2

# restore from image like so:
bzcat sda.img.bz2 | sudo dd of=/dev/sda
[/quote]

bzip2 is fairly slow on my system, probably because it only uses one processor at a time, but it has the advantage that you can continue working on the desktop in the foreground, or even watch a video in hd at the same time.

I also tested the same approach using the multi-threaded version of  version of bzip2 (pbzip2).  
This makes the process  of creating the compressed image much faster at the expense of slowing down any other foreground app.

The following are the actual commands used to back up and restore the partition, with the results below each command.   Using pbzip reduces the time by about 2/3 when creating the backup image, but does not improve writing the image by that much.
 
sudo dd if=/dev/sda5 | bzip2 > /media/peter/Backup/sda5.img.bz2
    ...16106127360 bytes (16 GB) copied, 1046.94 s, 15.4 MB/s
sudo dd if=/dev/sda5 | pbzip2 > /media/peter/Backup/sda5.new-img.bz2
    ...16106127360 bytes (16 GB) copied, 379.716 s, 42.4 MB/s

bzcat /media/peter/Backup/sda5.img.bz2 | sudo dd of=/dev/sda5
    ...16106127360 bytes (16 GB) copied, 962.37 s, 16.7 MB/s
pbzip2 -dc /media/peter/Backup/sda5.img.bz2 | sudo dd of=/dev/sda5, 
    ...16106127360 bytes (16 GB) copied, 707.127 s, 22.8 MB/s

My compression ratio is about 75%, on a partition with 50% free space.  In other words, in this instance a 16.1 GB partition has a 4.1GB compressed image (I expect this can vary a lot).

---

### Post by bardo2 on 2015-04-06
Congrats! And thx for letting us know about the ample details. Much appreciated.

gl, and have fun!

---

### Post by pmi2 on 2015-04-06
Thank YOU for your help.  

One could probably make a more general case for using this method as a backup alternative, although that is above my paygrade here.

It also occurred to me that one could use the Gnome-Disks utility to make an image which can be mounted as a file system if necessary, and compress old images using bzip2 or pbzip2 for archiving, but of course that is no longer a one-pass operation, so for my purposes, your suggestion works fine.

Thanks again.

---

