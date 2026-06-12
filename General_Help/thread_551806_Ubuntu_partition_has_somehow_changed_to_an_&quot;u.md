---
title: "Ubuntu partition has somehow changed to an &quot;unknown&quot; partition"
date: 2007-09-15
forum: General Help
---

### Post by mahasmb on 2007-09-15
For some reason unknown to me, my Ubuntu partition on my laptop has been changed to an ***_unknown_*** filetype. I can not access any of the files through any means. Not even Testdisk.

I'm at a great loss. I have no idea how to fix and how this even happened.


[http://ubuntuforums.org/showthread.php?t=548834](http://ubuntuforums.org/showthread.php?t=548834)

---

### Post by pheeror on 2007-09-15
It's hard to say way this happened without _any_ information. Actaully that partition type flag isn't much important and you can easily change it (e.g. fdisk). I guess you should be able mount that partition without correct filetype flag in partition table. Try boot some linux rescue live cd (systemrescuecd is brilliant) and find out if you can get your data - but this requires some knowledge.

---

### Post by randell6564 on 2007-09-15
> **mahasmb said:**
> For some reason unknown to me, my Ubuntu partition on my laptop has been changed to an ***_unknown_*** filetype. I can not access any of the files through any means. Not even Testdisk.

I'm at a great loss. I have no idea how to fix and how this even happened.


[http://ubuntuforums.org/showthread.php?t=548834](http://ubuntuforums.org/showthread.php?t=548834)
Are you Dual-Booting with Windows?  Because if you are not, then this does not make sense.  How is your Drive set up?  Is Ubuntu the only OS on your Box?

---

### Post by mahasmb on 2007-09-15
Yes, I'm dual booting with Windows XP. 

And all the info should be in the page I linked.

---

### Post by randell6564 on 2007-09-16
> **mahasmb said:**
> Yes, I'm dual booting with Windows XP. 

And all the info should be in the page I linked.
Well, I'm going say that your first mistake was "backing up" your fiesty install!   Why would you Zip an entire OS anyway?  IMHO, you zipped something, ie..an Executable file, and NOW it cannot EXECUTE!

---

### Post by randell6564 on 2007-09-16
> all I did was get 3ddesk working, change my Gnome themes, and backup my Feisty install by zipping everything into a .bz2 file. This is a pretty good place to start.  Especially since > 
Everything was fine the other day.

---

### Post by mahasmb on 2007-09-16
Finally, we're getting somewhere.

But I would like to point out that I followed this HOW TO : [http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+restore&page=37](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+restore&page=37)

And no one else has experienced my problems.

Also, since zipping anything is a two step process whereby the files are copied *and then* placed in the zipped folder, I do not see why this would cause any harm to the initial copies of the files. Unless I'm missing something.

---

### Post by randell6564 on 2007-09-16
> Also, since zipping anything is a two step process whereby the files are copied and then placed in the zipped folder, I do not see why this would cause any harm to the initial copies of the files. Unless I'm missing something.  You are correct my friend.  Sorry!

---

### Post by atlfalcons866 on 2007-09-16
what file system was it before it changed to unknown partition?

---

### Post by randell6564 on 2007-09-16
> **atlfalcons866 said:**
> what file system was it before it changed to unknown partition?
AND, if it's an "unknown partition"  then you MUST be using Windows when trying to view it.  Windows cannot identify Linux partitions.
Are you trying to access your Linux files from Windows?

---

### Post by randell6564 on 2007-09-16
> Are you trying to access your Linux files from Windows?Scratch that!  
when you partitioned your drive, what filesystem did you use for your Linux partition?

---

### Post by mahasmb on 2007-09-16
Whatever file system Feisty installs with. I think ext2, maybe ext3.

And no, Testdisk tells me it's an unkown filesystem. And when I put in my Ubuntu CD and go reach the partition manager it also tells me that it's an unknown filesystem. So does Super Grub Disk, I think.

---

### Post by randell6564 on 2007-09-16
This is the strangest thing I've seen yet!  There is nothing that I know of short of a VIRUS that can change a filesystem!  And even a VIRUS cannot actually CHANGE it. It can only make it APPEAR as something that it is not.
This is very interesting.  I'm going to do some googling and see if I can find something similar to your situation.  In the mean time, can you please provide the specs on your LapTop?

---

### Post by mahasmb on 2007-09-16
Sure thing. Thank you very much.

1.46 Celeron M 410 Processor
512 DDR2 SDRAM
60 GB (Half Windows XP half Ubuntu Feisty Fawn)
ATI Radeon Xpress 200M

---

### Post by bonestonne on 2007-09-16
linux can read Fat32/NTFS
Windows cannot read Ext2/Ext3

using Apple or Windows to fix a Linux partition will not work. you'll have to use a Live CD to format the partition to Ext3, and then copy the .bz2 file onto the partition, extract it, and put it in place. technically, a fresh install would be better, however having all of your stuff working is a reason not to i suppose. when i get a new drive i know i wont like it, having a triple boot setup with Ubuntu x64 will not be a joy to do over.

back up often and make text files of how you make things work. sounds silly, but when you need reference quick, you've got it.

---

### Post by randell6564 on 2007-09-16
Sure thing!  Hang tight my friend.  I'm searching!
Bear with me, I need to ask.,
You have this LapTop that came with Windows correct?  And you decided to add Linux and dual-boot?   Or did you completely wipe your HD, partition it and install Windows then Linux?
You said that "everything was fine".  Were you ever able to boot into Linux after installing, or did this happen right after the first restart?

Do you have a Windows CD, or did your laptop come with an OEM version?
Forgive me. I know that all these questions are frustrating but in order to get to the root of the problem, we all have to SEE things from the begining.
How was your HD partitioned BEFORE you decided to add Linux?

---

### Post by randell6564 on 2007-09-16
> **bonestonne said:**
> linux can read Fat32/NTFS
Windows cannot read Ext2/Ext3

using Apple or Windows to fix a Linux partition will not work. you'll have to use a Live CD to format the partition to Ext3, and then copy the .bz2 file onto the partition, extract it, and put it in place. technically, a fresh install would be better, however having all of your stuff working is a reason not to i suppose. when i get a new drive i know i wont like it, having a triple boot setup with Ubuntu x64 will not be a joy to do over.

back up often and make text files of how you make things work. sounds silly, but when you need reference quick, you've got it.
But the 'Million Dollar' Question here is; HOW does an EXT2/3 filesystem get CHANGED so that it cannot be identified?  This was an exsisting OS that upon rebooting was rendered inaccessable due to grub not being able to identify the requested partition.

---

### Post by mahasmb on 2007-09-16
> **randell6564 said:**
> Sure thing!  Hang tight my friend.  I'm searching!
Bear with me, I need to ask.,
You have this LapTop that came with Windows correct?  And you decided to add Linux and dual-boot?   Or did you completely wipe your HD, partition it and install Windows then Linux?
You said that "everything was fine".  Were you ever able to boot into Linux after installing, or did this happen right after the first restart?

Do you have a Windows CD, or did your laptop come with an OEM version?
Forgive me. I know that all these questions are frustrating but in order to get to the root of the problem, we all have to SEE things from the begining.
How was your HD partitioned BEFORE you decided to add Linux?

Yes, it initially came with Windows and I only have the Recover CD. It was setup so that Windows would take up only 30 GB from the start. And leave the other 30 GB untouched. I added Linux to it months ago, and both operating systems have been working fine* until the day I decided to make a backup by zipping everything in my Ubuntu partition. I, however, stored the zip file onto my Ubuntu partition, because I did not have space in my Windows partition and was planning on burning everything onto a DVD-RW.

So, when I installed Ubuntu months ago, I just used those 30 GB that were untouched by Windows. I didn't have to partition or delete anything.

*Windows has been working, but after I installed all my programs and set it up as I liked, with still half the Windows partition unused, it just became unbearably slow. Everything worked, but even to open my Start menu took forever. I was also even able to (months ago) do a fresh install of Windows and leave my Ubuntu untouched, but again Windows within days became slower than a snail. So it just meant that I never booted into Windows and only used my Linux partition.

---

### Post by randell6564 on 2007-09-16
> **mahasmb said:**
> Yes, it initially came with Windows and I only have the Recover CD. It was setup so that Windows would take up only 30 GB from the start. And leave the other 30 GB untouched. I added Linux to it months ago, and both operating systems have been working fine* until the day I decided to make a backup by zipping everything in my Ubuntu partition. I, however, stored the zip file onto my Ubuntu partition, because I did not have space in my Windows partition and was planning on burning everything onto a DVD-RW.

So, when I installed Ubuntu months ago, I just used those 30 GB that were untouched by Windows. I didn't have to partition or delete anything.

*Windows has been working, but after I installed all my programs and set it up as I liked, with still half the Windows partition unused, it just became unbearably slow. Everything worked, but even to open my Start menu took forever. I was also even able to (months ago) do a fresh install of Windows and leave my Ubuntu untouched, but again Windows within days became slower than a snail. So it just meant that I never booted into Windows and only used my Linux partition.
I'm going to venture to say that you goofed things up when you ZIPPED!  [check this out]("http://www.linuxforums.org/forum/ubuntu-help/103480-file-system-changed-now-i-cannot-boot-ubuntu.html#post508345")

---

### Post by mahasmb on 2007-09-16
This is pretty much the command I used:

```
tar cvpjf backup.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/backup.tar.bz2 --exclude=/mnt --exclude=/sys --exclude=/media /
```

---

### Post by randell6564 on 2007-09-16
> **mahasmb said:**
> This is pretty much the command I used:

```
tar cvpjf backup.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/backup.tar.bz2 --exclude=/mnt --exclude=/sys --exclude=/media /
```Yes but did you check my [link? ]("http://www.linuxforums.org/forum/ubuntu-help/103480-file-system-changed-now-i-cannot-boot-ubuntu-new-post.html") Maybe it's just a Bios thing.

---

### Post by mahasmb on 2007-09-17
Yes, I looked into exactly that before and my BIOS doesn't give me any of those options, because I have PhoenixBIOS and not Phoenix Award BIOS.

---

### Post by mahasmb on 2007-09-17
I give up. I'm doing a fresh install and hoping this doesn't happen to me again.  I guess I'll be spending the next week getting my drivers, internet and such set up. This was the whole point of backing up everything in the first place. ](*,)

 ](*,)

 ](*,)

:cry:

---

### Post by randell6564 on 2007-09-17
> **mahasmb said:**
> I give up. I'm doing a fresh install and hoping this doesn't happen to me again.  I guess I'll be spending the next week getting my drivers, internet and such set up. This was the whole point of backing up everything in the first place. ](*,)

 ](*,)

 ](*,)

:cry:
I don't get it.,I install and RE-install all flavors of Ubuntu on my various Pc's.  (From old to New)  and Never had to go searching for Drivers.  "Internet" just Worked right out of the box. (Linksys Wusb11 ver.2.6) The only problems that I recall encountering are Dependancy issues.  And I could always work around that by just finding something else to satisfy my needs.

I am very sorry that we could not help you through this my friend.  But let me suggest that you not fool around with something that is not broke next time.  3DDesktop is just Candy!  And can have some really adverse affects on your Xserver if your hardware is not compatible and/or Old.
IMHO, Backing up an entire OS is useless!  Especially when you already HAVE it on CD! OR can get any software that you installed AFTER initial installation from the Repo's.  I understand that you were attempting to copy an Operating System that was created to your specs.  But really, what good is that unless you know Exactly how to format your drive, unzip your OS and place EVERYTHING in it's proper place?  Because if you don't, it will not work anyway!

But then again, I really don't know sh*# about this kind of stuff!  

**Reinstall and Leave it alone (While it's working).**Until you get a good idea of what your board is capable of.

---

