---
title: "[SOLVED] Enlarging NTFS partition with Gparted: 12GB of data loss"
date: 2008-03-11
forum: General Help
---

### Post by perixx on 2008-03-11
Hi!

I've been posting parts of this in another thread already, but it may have been misplaced there ('ntfscloned XP freezes')...
I was able to find a solution to that, but when resizing (enlarging) the cloned NTFS partition (26GB) to it's host's actual size (34GB), an amount as large as 10GB was blown from my 'documents and settings' folder! 

Weird: all facts indicate that the data's still in place - there's still about 17GB of the partition in use. Could this be a problem with the partition table or the NTFS 'root entries folder', if there's some such thing?

What could be the cause and what might be done about this? I even can't completely wipe the data at the moment, to free the disk space... 

Thanks for help!

perixx

---

### Post by gobbles414 on 2008-03-11
> **perixx said:**
> Hi!

I've been posting parts of this in another thread already, but it may have been misplaced there ('ntfscloned XP freezes')...
I was able to find a solution to that, but when resizing (enlarging) the cloned NTFS partition (26GB) to it's host's actual size (34GB), an amount as large as 10GB was blown from my 'documents and settings' folder! 

Weird: all facts indicate that the data's still in place - there's still about 17GB of the partition in use. Could this be a problem with the partition table or the NTFS 'root entries folder', if there's some such thing?

What could be the cause and what might be done about this? I even can't completely wipe the data at the moment, to free the disk space... 

Thanks for help!

perixx


I've never been a big believer in resizing partitions, for the precise reason that it call lead to data loss. This is especially true of Windows partitions, since fragmentation is such a huge problem in Windows.  I know that resizing is the often the only option for people who want to dual-boot Windows and Ubuntu, because Micro$oft prefers system recovery utilities over full operating system installation disks. But resizing should still be used only as a last resort, IMHO.

Do you have backups for all of your important data? If so, I recommend that you use a program like [GWSCAN]("http://support.gateway.com/support/drivers/search.asp?param=gwscan&st=kw") to "write zeros" to your entire hard drive. Then install Windows (if you need it). Do a defrag and error check. Then install Ubuntu.

---

### Post by perixx on 2008-03-12
Hi gobbles414!

My case here is a little bit special:


I've cloned the whole XP partition, so the lost data is not so important - more important to me is, how to free up the 'missing' space that's still occupied by that data... perhaps I should try to run testdisk on it.

I can't understand though, why I'm encountering data loss, when ENLARGING partitions (i.e. adding space on its end)!
Besides, the very sense of cloning XP would be nullified, if I was to zero out the cloned partition, which was difficult enough to come by getting it to work..! :)


To use Ntfsclone, I needed to create a partition, larger than the cloned system. In order not to waste the remaining space, I then enlarged that partition to it's host-partition's size (about 8GB larger). What still puzzles me, is how the 'Windows quick format NTFS' and the Gparted NTFS-format differs, and if it does matter which of those I use for the mentioned purpose. 

Also, from what I've read so far, shrinking partitions with Gparted (after XP partition has been defragmented), to make room for Ubuntu, seems to work without too much trouble mostly. That's why I'm wondering how I need to re-launch MS' 'fixboot' and 'chkdsk' after enlarging the cloned partition...


perixx

---

### Post by wieman01 on 2008-03-12
**Partimage** has similar issues. When you restore to a partition that is larger than the originial one, you lose space. Solution is to restore to a partition of the exact same size and then enlarge it the cloned partition, no earlier. Could this be the issue?

---

### Post by perixx on 2008-03-17
Hello Wieman01!

Sorry for the late reply, but I was doing some thorough cloning crash-course the last few days!!

In the end, it turned out to be a false alarm, sorry..! The questionable data wasn't really lost, but well-hidden and it was inaccessible from the explorer (thus, also not being shown in the 'used space' diagram of Easycleaner.

I suppose, that I was copying this data into XP with Linux back then; obviously the whole folder had wrong user ownership rights - claiming the folder's ownership in XP pro admin account did the job! Speaking of bad ownership: I can't quite see why I need to change the ownership of a freshly formatted NTFS partition to USER, before I can apply any image to it with 'ntfsclone' - and if there are any possible drawbacks to expect under XP, then...

Anyway, I was able to rip a XP partition several times by now, producing an instantly working clone :))

Was a hard piece of work to figure out the exact procedure that worked, though..!!

Btw., producing a partition of exactly the size the original one has, is not so trivial... Gparted isn't providing a sector-based mode and I don't know how to use sfdisk/cfdisk or whatever, to do such a thing! Perhaps you know how to do it? But even then, chances are good that one has to 'repair' an exact clone partition, that's being resized later, I guess. 

  
perixx

---

### Post by wieman01 on 2008-03-18
> **perixx said:**
> Btw., producing a partition of exactly the size the original one has, is not so trivial... Gparted isn't providing a sector-based mode and I don't know how to use sfdisk/cfdisk or whatever, to do such a thing! Perhaps you know how to do it? But even then, chances are good that one has to 'repair' an exact clone partition, that's being resized later, I guess. 
Hello, 

No, the only tool I have experience with is GParted. And it worked fine for me. You are right in that it does not provide a sector-based mode, however, that has not been a big issue for me so far. The partition does not have to be the exact same size when you use Partimage. A few MBs larger than the originial one does not hurt, you simply lose a few MBs of disk space, that's all.

---

### Post by Herman on 2008-03-18
:) Hello perixx and wieman01,
I am a frequent user of both GParted and Partimage, and I have had no problems with either of them. Normally I would restore a Partimage backup to a partition of equal size or larger than the partition it came from.

When we restore a partimage backup of an ext3 file system to a partition that's much larger than the one the partition the file system originally came from, an interesting thing happens. 
The file system is still the same, but the partition is quite large. After adding some files we might find that that we *appear to* run out of room much sooner than expected. 
This is because the file system has not been resized to fill the partition.

With an ext3 file system, the way to fix that is to run the command 'sudo resize2fs -p /dev/hda2', and the file system will be resized to fill the partition. (Where /dev/hda2 is the partition containing the file system you want to work on, of course).

I would try running CHKDSK from a Windows [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") and see if I could find out the appropriate options to run that with. I think there are only two options for CHKDSK, but I can't remember them.

Regards, Herman :)

---

### Post by wieman01 on 2008-03-18
Hello Herman, 

Good call, thank you very much for:
> sudo resize2fs -p /dev/hda2
I did not know how to fix it, so I usually restore the image to a partition of the exact same size and would then resize the partition. This works, but is less elegant than the solution you have pointed out.

---

### Post by perixx on 2008-03-20
Hello Herman ;)

Well, in my particular case, I've just created a partition significantly larger than the origninal one, because I needed more space anyway. Just like Herman has pointed out, the 'extended' part of the 'containing' target partition (in NTFS) won't be recognized by the cloned Windows by default. I'm not exactly sure which step led to success (I was doing several different steps, some combined, some each alone and everything in different order, a few times). 

So far, every time  the NTFS partition was resized (with Gparted), Windows wouldn't boot anymore in the first place. Running the recovery console, logging into the Windows session and doing ```
chkdsk c: /r
``` was needed afterwards, and probably also 'fixmbr c:' (and perhaps also 'fixboot', although I've encountered several issues of Windows not booting into the cloned partition at all after that). I'm pretty sure, though, that 'fixntfs' in Ubuntu didn't help much...

regards,


perixx

---

### Post by Herman on 2008-03-20
:)  Hello wieman01, 
You are welcome, thank you for your kind and polite feedback.
I think these commands for resizing the file system date back to a few years ago when there were programs for resizing the partition only, such as fdisk, and users always had to use the file system commands seperately to adjust their file systems inside the partitions. Nowadays things are more automated, we're used to having things done for us, and we've all forgotten some of the commands because we rarley need them anymore. They still come in handy sometimes though.

:) Hello perixx, 
Thanks for sharing your 'chkdsk c: /r'. I'll remember that, cheers!

Your 'fixntfs' got me thinking.
I was wondering if there's an ntfs file system checking program for Linux....
Someone in another thread was asking about that too.

I just ran a search for ntfsprogs in Synaptic, and there's quite a few programs under developement for NTFS support in Linux.

**ntfsfix **is the Linux file system checker to NTFS, although it doesn't claim in the documentation to be as effective as Windows' own CHKDISK, I would imagine it will probably be improving steadily, and may be as good or better sooner or later.

**mkntfs** is the Liunx command for making a new NTFS file system in a partition.

**ntfsresize** is the Linux command (program) for resizing an NTFS file system to fill a cloned partition.

There are quite a number of other useful looking commands there too, too many to list here. 
For the full list:
```
man ntfsprogs
```...so now I know, I should have advised you to use ntfsresize from Ubuntu. :)

It's noteworthy to point out though, that the good folks at GParted LiveCD themselves do suggest in their documentation, (at least at the time when their documentation was written), to run CHKDSK from Windows after using GParted LiveCD for resizing any partition containing an NTFS file system. [How to Resize a Partition]("http://gparted.sourceforge.net/larry/resize/resizing.htm") (GParted LiveCD).

Regards, Herman :)

---

### Post by perixx on 2008-03-21
Hello again!

> ntfsfix is the Linux file system checker to NTFS Yep, that's the program I actually mean, not 'fixntfs', sorry :]

> ntfsresize isn't that one included in Gparted? Or is this using some other routine/subprogram? Interesting, that the Gparted-dev's suggest to use MS' 'chkdsk' after resizing, instead of 'ntfsfix'...

Btw., I've been making a slight progress in the 'memory stick' topic I've posted you about:
[http://ubuntuforums.org/showthread.php?t=722242]("http://ubuntuforums.org/showthread.php?t=722242") 

regards,

perixx

---

### Post by Herman on 2008-03-21
> ntfsresize                                  isn't that one included in Gparted? Or is this using some other routine/subprogram? Interesting, that the Gparted-dev's suggest to use MS' 'chkdsk' after resizing, instead of 'ntfsfix'...It all depends on what GParted you are using, (where you got it from).
There is [GParted -- LiveCD]("http://gparted.sourceforge.net/"), which would come with ntfsprogs already installed in it, and then there is the Ubuntu 'Desktop' Live/Install CD, which would also need to have ntfsprogs, but possibly not be as up to date as GParted's own LiveCD.
Then there is Gnome Partition Editor (GParted) in Ubuntu, which you can install yourself in your hard disk installed operating system. I always install it. You need to install ntfsprogs yourself as well if you want it in that case, or else most NTFS functions will be 'greyed out' in Gnome Partition Editor.

Documentation is often out of date as well, because Linux software is always progressing so fast, it's hard for the documentation to keep up with it. Possibly ntfsfix is just as good as or better than CHKDSK these days, it depends on when that documentation was last updated, and the author of the documentation probably likes to err on the side of caution as well. No-one wants to risk being blamed for anyone else's data loss.
I think ntfsprogs and GParted must be pretty good, a lot of people per day are using them to resize their partitions with and there are very few reports of problems in porportion to the amount of useage the software must be getting.

> Btw., I've been making a slight progress in the 'memory stick' topic I've posted you about:
[http://ubuntuforums.org/showthread.php?t=722242](http://ubuntuforums.org/showthread.php?t=722242) 
Cool, sorry I couldn't be more help to your with flash memory data recovery, you might end up teaching me instead.
I'm have two identical USB flash memory sticks and I'm making then into Ubuntu demonstration units. I have already made one with Ubuntu installed in it according to, [HOW TO make a USB Disc with Ubuntu LiveCD and Super Grub Disc in it.]("http://ubuntuforums.org/showthread.php?t=575406&highlight=super+grub+disk+usb") I am installing lots of software and games, to impress people who have never tried out Ubuntu before. I will make one of them and then clone it to the other SUB flash memory stick with your dd command or a similar one. That will save me a lot of work.
I also have used dd commands before for copying discs and partitions. Here's a link to my favourite web page about the dd command, [Learn the DD command]("http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/"), by AwesomeMachine.

Regards, Herman :)

---

