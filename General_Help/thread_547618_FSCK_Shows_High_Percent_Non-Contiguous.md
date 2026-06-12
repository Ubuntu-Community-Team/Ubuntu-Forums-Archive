---
title: "FSCK Shows High Percent Non-Contiguous"
date: 2007-09-10
forum: General Help
---

### Post by Ingla on 2007-09-10
Hello.

I have my home directory on a separate partition, which is checked automatically every 24th boot. It often gets stuck for a while and then moves on. The summary at the end shows over 20% non-contiguous and growing.

On Windows, I have programs to deal with this, but have never encountered the problem on Linux. I expect this is detrimental to efficient functioning of the file system and will probably slow things down increasingly.

Can anything be done to safely compact the files?

Thanks.

---

### Post by fjgaude on 2007-09-10
I wonder, how full is your home partition? If it is near full, like 90% and you have lots of very large files, music, video, etc., the ext3 filesystem has trouble auto arranging the files and fragmentation is the result.

frank

---

### Post by tszanon on 2007-09-10
> **fjgaude said:**
> I wonder, how full is your home partition? If it is near full, like 90% and you have lots of very large files, music, video, etc., the ext3 filesystem has trouble auto arranging the files and fragmentation is the result.

frank
I second that. It was the first thing that came to my mind.
EXT3 defrags itself during normal use. It doesn't need any external application to defrag itself. But, as the free space decreases, it becomes less and less capable of doing it. Free some space and it the problem is likely to disappear over time.

---

### Post by Ingla on 2007-09-10
The home folder has about 300 Gb total. I'm not sure how much is actually usable as different outputs say various things. Depending on where you take the data from it is between 50% and 55% full. So, I don't think the problem could be lack of free disk space. There are lots of large files.

Is it possible the file system just can't handle large disks  ... even if the space used is not high when taken as a percentage? That would seem to be a serious problem, as computer technology will probably support larger and larger disks. If I understand correctly, you're saying this wouldn't be a problem with any distro but, rather, with EXT3 itself. This also implies that the only way to prevent continued fragmentation is not to use the disk or to put Windows on it (gulp) because I could fix the fragmentation and rearrange files for contiguous use of space.

Can this be true?

---

### Post by fjgaude on 2007-09-10
I'm no expert on filesystem design, but ext3 is about as good as it gets. It defrags on the fly if it has enough free space to do it. As far as I know all the various filesystems used by the various distros use the same technique at handling defragmentation. The Linux ext3 can handle all modern disks into 100s of terabyte sizes... think of the servers with their 12-drive raid arrays, with each drive being 500GB. <smile>

Windows NTFS is not good and that is why you have to defrag it all the time with an external program, and the one that comes with XP is not that good. The only one I know of that does it right is Diskeeper from Executive Software (which has been bought out recently).

So, just how big are some of the files you have placed on your drive array? How many have you deleted?

frank

---

### Post by Ingla on 2007-09-10
The largest are video files which could be anywhere from 300Mg - 1.5Gb each. The average is probably 700Mb - 800Mb. Actually, I delete all the time and try to keep over 130Gb free at any one time. I also add new ones. The files that are there are ones I want for one reason or another ... at least for the time being. 

I understand what you're saying about NTFS and agree. BUT at least it IS fixable  It seems EXT3 isn't. The only way would be to delete files I don't want to delete yet (and stop adding new ones - i.e., stop using the disk) and hope the system fixes itself.

If you're working with large files, there should be some way to maintain the system. Maybe fsck could do that, but I've always been afraid to try running it manually. I might (through ignorance) run it on a system with write permissions or something and who knows what would happen.

---

### Post by fjgaude on 2007-09-10
Okay, I see nothing wrong with running fsck on the disk, but not while it is running. Run LiveCD and then run fsck from there to the /dev/xxx mounted from the CD. Understand?

frank

---

### Post by Alex1770 on 2007-09-10
Ingla, can you post the output of the command ```
df
```? (You need to open a terminal to do this.)

To answer your question, the filesystem (ext3) has no trouble handling large disks and large files. Are you sure there is a problem? Have you noticed a loss of performance?

---

### Post by digitalbenji on 2007-09-10
you may want to make that df -h so the results show some nice human numbers for those not liking byte notation.

---

### Post by Ingla on 2007-09-10
Results:
-------------------------------------------------------------------------------------------
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             7.4G  3.5G  3.6G  50% /
varrun                506M  112K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  116K  506M   1% /proc/bus/usb
udev                  506M  116K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-16-generic/volatile
/dev/hda5             285G  143G  128G  53% /home
/dev/sda1              30G   22G  7.7G  74% /media/sda1
/dev/sda5             120G   14G  106G  12% /media/sda5
10.0.0.2:/home/aba    7.6G  5.0G  2.3G  69% /media/Ubuntu-Shared
---------------------------------------------------------------------------------------------

The partition in question is hda5.

As for fsck, I have an old Live Disk (from Breezy?), but have never used it except to see what Ubuntu was about. Once I tried to test for some problem, but it was only giving me output for the CD itself not the hard drive. I guess I don't know how to use it.

I know about the problem from the console readout. After booting 24 times fsck runs and reports noncontiguous disk use at 20%+ when it's finished ... before Ubuntu continues to load.

There is some slowness. This is a pretty new machine 4.4 dual core cpu with 1 Gg RAM and a new hard disk (don't remember the speed offhand). It should run plenty fast.

---

### Post by tszanon on 2007-09-10
I think that, unless there is a noticeable performance loss, there's no need to worry about it.
I'd just keep an eye on it, just to know how things progress. Maybe it will stuck at 20%, maybe it will even decrease.

---

### Post by Herman on 2007-09-10
> As for fsck, I have an old Live Disk (from Breezy?), but have never used it except to see what Ubuntu was about. Once I tried to test for some problem, but it was only giving me output for the CD itself not the hard drive. I guess I don't know how to use it.Ubuntu Live CDs are good to use for fdisking your file systems if you can use the command line a little bit.

The best Live CD to use for partitioning and file system work is [GParted --LiveCD]("http://gparted.sourceforge.net/"), it's free and only a small download. With GParted LiveCD you can click on the partition you want checked and just click 'Check' on the right-click menu. Wait a while and it will be done for you. If you click on the triangular butttons to expand the info boxes, you will see a full report of what GParted is doing and/or has done for you. It's great! :)

If you want to, later when you feel like it or have time you can read the man page for e2fsck, which is the command that fsck will run for you if you have an ext3 file system. 
If you can understand the man page or even if you don't, but have time to experiment a little you will soon be able to come up with your own customized commands for file system checking.
I already did some of the searching, reading and experimenting for most Ubuntu users and typed out what I learned in a web page.  I'm not a file system expert, just another user who is learning stuff, but who has a website. You can get a head start here if you like, I have my favorite commands.shown here on this page,  [File Systems and Mounting Page]("http://users.bigpond.net.au/hermanzone/p10.htm")  Mounting other filesystems and taking care of them.
The information on that page has saved my butt and a few other people's butts already. I hope you find it helpful. :)

Regards, Herman :)

EDIT: > df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             7.4G  3.5G  3.6G  50% /
varrun                506M  112K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  116K  506M   1% /proc/bus/usb
udev                  506M  116K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-16-generic/volatile
[COLOR=Red]** /dev/hda5             285G  143G  128G  53% /home**[/COLOR]
/dev/sda1              30G   22G  7.7G  74% /media/sda1
/dev/sda5             120G   14G  106G  12% /media/sda5
10.0.0.2:/home/aba    7.6G  5.0G  2.3G  69% /media/Ubuntu-SharedTry running this command from a Ubuntu LiveCD, it will probably clear up your problem, 
```
sudo e2fsck -y -f -v /dev/hda5
```I'm not sure if it will matter much, but if possible  I think you should try to use a newer LiveCD than Breezy, just in case the hard working devs have improved file system utilities since those days. It's usually best to use up to date software.

---

### Post by fjgaude on 2007-09-10
> As for fsck, I have an old Live Disk (from Breezy?), but have never used it except to see what Ubuntu was about. Once I tried to test for some problem, but it was only giving me output for the CD itself not the hard drive. I guess I don't know how to use it.

Take any rescue disk, LiveCD Ubuntu, SystemRescure, Knoppix, PMagic, anything that you can boot into, and from there sudo mount /dev/hda5 /mnt/hda5 and then run sudo fsck  /dev/hda5.

frank

---

### Post by Ingla on 2007-09-10
Thanks for all the help. I'll look into doing this (probably download a newer cd).

> **fjgaude said:**
>  sudo mount /dev/hda5 /mnt/hda5 and then run sudo fsck  /dev/hda5.

Will this mount it read only or do I have to type something about that also like:

```
mount -r or mount -o ro /dev/hda5 /mnt/hda5
```

Is it true that running fsck on a file system with write permission can wreck it?

---

### Post by Herman on 2007-09-11
> Will this mount it read only or do I have to type something about that also like:

 	Code:
 	mount -r or mount -o ro /dev/hda5 /mnt/hda5 
Is it true that running fsck on a file system with write permission can wreck it? You should never run a file system check on a file system while it is mounted.

---

### Post by Ingla on 2007-09-11
It shouldn't be mounted at all? So, how do you fsck it from a Live Disk?

---

### Post by vanadium on 2007-09-11
As said before: you just specify the drive as /dev/hda5

"not mounted" means that you cannot access the files on the disk from within your file system. /dev/hda5 is there, mounted or not, as you can tell from the command "sudo fdisk -l"

I am not sure how running fsch could  reduce the fragmentation, tough. In fact, I am not sure if the fragmentation you experience is in fact a problem. You are dealing with big files. It probably won practically hurt performance if these big files are stored in two or three big separate chunks. Fragmentation is only significant if it concerns files stored in many very small chunks.

---

### Post by fjgaude on 2007-09-11
> **vanadium said:**
> As said before: you just specify the drive as /dev/hda5

Yes, you are right, just fsck /dev/hda5 from the LiveCD... that should do it.

Sorry about suggesting to mount the drive, not good, lost my mind, memory. <smile>

frank

---

### Post by Herman on 2007-09-11
A file system check is something different from defragging, the only similarities are that they are both jobs you do to file systems and the user has to wait for a while for the process to be completed. 
But a file system check has not much  else in common with defragging really. 
Linux file systems never need defragging. 

[CENTER][SIZE=4][B][Why Linux filesystems never need defragging.]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting")
[/B][/SIZE][LEFT]
EDIT 1: To be more correct, Linux file systems can  become fragmented, I am told, but only after they are filled to more than about 80% or 90%. The best thing to do about it if that happens would probably be to remove files or increase the size of the file system. When someone says they 'never need defragging' they are pretty near right.
[/LEFT]
 [/CENTER]
 
Some 'file system checks' just take a quick look at your superblock to see if a bigger check is needed or due, some file system checks will  'preen' your file system, and other file system checks can repair little problems, or even repair serious problems, depending on the options you specify when you type in the command. 
However. most people don't really need to learn those, because unless you have a habit of shutting your computer down wrong, or your hard disk is on its way out, problems with Linux file systems are rare. Anyway you can get help right here if you do have a problem. :)
EDIT 2: It isn't always the user's fault if file system needs a little extra maintenance, power interruptions can cause file system damage and so can regular wear and tear. I have read that file sharing programs can test a file system's resilience pretty well.

Regards, Herman :)

---

### Post by psusi on 2007-09-12
> **tszanon said:**
> 
EXT3 defrags itself during normal use. It doesn't need any external application to defrag itself. But, as the free space decreases, it becomes less and less capable of doing it. Free some space and it the problem is likely to disappear over time.

No, it does not defragment itself; the linux kernel simply uses a non brain dead allocation algorithm to prevent insane levels of fragmentation, unlike windows.  

If you wish to defrag an ext3 partition, you can install the defrag package and run e2defrag on the unmounted block device, but you most likely will not be able to tell any difference since most likely, those files that are fragmented are large files that are only broken into 2-3 large chunks, not 2,000 different fragments per file common on windows.  

> **fjgaude said:**
> I'm no expert on filesystem design, but ext3 is about as good as it gets. It defrags on the fly if it has enough free space to do it. As far as I know all the various filesystems used by the various distros use the same technique at handling defragmentation. The Linux ext3 can handle all modern disks into 100s of terabyte sizes... think of the servers with their 12-drive raid arrays, with each drive being 500GB. <smile>

Windows NTFS is not good and that is why you have to defrag it all the time with an external program, and the one that comes with XP is not that good. The only one I know of that does it right is Diskeeper from Executive Software (which has been bought out recently).

So, just how big are some of the files you have placed on your drive array? How many have you deleted?

frank

Again, ext does not defrag itself.  It doesn't really have anything to do with the filesystem itself, rather it is how the kernel chooses to allocate new blocks.  Windows uses an algorithm that has been known to be the worst possible way for 30 years, and that causes absurd levels of fragmentation very quickly.  Linux uses algorithms that resist fragmentation and keep the number of fragments to a minimum.  

Fragmentation only has a significant impact on performance once files begin to have a great many small fragments.  You won't notice any loss on a 1 gig file that has 4 250 MB fragments.

---

### Post by tszanon on 2007-09-13
> **psusi said:**
> No, it does not defragment itself; the linux kernel simply uses a non brain dead allocation algorithm to prevent insane levels of fragmentation, unlike windows.  

If you wish to defrag an ext3 partition, you can install the defrag package and run e2defrag on the unmounted block device, but you most likely will not be able to tell any difference since most likely, those files that are fragmented are large files that are only broken into 2-3 large chunks, not 2,000 different fragments per file common on windows.  



Again, ext does not defrag itself.  It doesn't really have anything to do with the filesystem itself, rather it is how the kernel chooses to allocate new blocks.  Windows uses an algorithm that has been known to be the worst possible way for 30 years, and that causes absurd levels of fragmentation very quickly.  Linux uses algorithms that resist fragmentation and keep the number of fragments to a minimum.  

Fragmentation only has a significant impact on performance once files begin to have a great many small fragments.  You won't notice any loss on a 1 gig file that has 4 250 MB fragments.
So, would it be correct to say that in Linux you don't need defragging, no matter what file system I use?

---

### Post by psusi on 2007-09-13
It's a subjective statement, not objective.  Technically you don't NEED to defrag any system.  Practically though, you should almost never see any actual performance loss on a linux system due to fragmentation.  

If you really like watching the blocks move around and get all nicely packed in order, you can install the defrag package on the livecd and run e2defrag and it will compact it.  It even has the ability for you to specify the order of files so you can put some near the start and some near the end if you wish, but you will be hard pressed to notice any performance change.  

The defrag package was originally written by Linus and a few others back in like 1990, but it has fallen into such disuse and not been maintained over the years that hardly anyone remembers it, because nobody ever needs it.

---

### Post by tszanon on 2007-09-13
> **psusi said:**
> It's a subjective statement, not objective.  Technically you don't NEED to defrag any system.  Practically though, you should almost never see any actual performance loss on a linux system due to fragmentation.  

If you really like watching the blocks move around and get all nicely packed in order, you can install the defrag package on the livecd and run e2defrag and it will compact it.  It even has the ability for you to specify the order of files so you can put some near the start and some near the end if you wish, but you will be hard pressed to notice any performance change.  

The defrag package was originally written by Linus and a few others back in like 1990, but it has fallen into such disuse and not been maintained over the years that hardly anyone remembers it, because nobody ever needs it.
That's a good explanation. Thanks!

---

