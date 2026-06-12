---
title: "Program for 1-way Folder Sync?"
date: 2004-12-06
forum: General Help
---

### Post by killerfish on 2004-12-06
I have a dual boot system.  I'd prefer Linux, my wife prefers Windows.  I'm looking for program that I can run when Linux starts that will do folder synchronization with the My Picture's folder in my windows installation.  It needs to be 1 way since my windows partition is NTFS.  

Net, here's what I'd like to do.  When Linux starts, it will find any changes I made below My Picutres on my windows partition and copy them to a my_documents folder on my Linux partition.  Then, say I download some pics in Linux to this folder.  Finally, when I reboot to windows, I'd like windows to do a similar copy from my ext3 partition...  This way, my wife and I will always be able to work in our preferred environment and have access to the same data.  Plus, we'll have data redundancy and backups.    BTW, I do have read access to my ext3 partition in Windows via an L: drive....

Thanks!
KF

---

### Post by killerfish on 2004-12-06
[QUOTE=killerfish]I have a dual boot system.  I'd prefer Linux, my wife prefers Windows.  I'm looking for program that I can run when Linux starts that will do folder synchronization with the My Picture's folder in my windows installation.  It needs to be 1 way since my windows partition is NTFS.  

Net, here's what I'd like to do.  When Linux starts, it will find any changes I made below My Picutres on my windows partition and copy them to a my_documents folder on my Linux partition.  Then, say I download some pics in Linux to this folder.  Finally, when I reboot to windows, I'd like windows to do a similar copy from my ext3 partition...  This way, my wife and I will always be able to work in our preferred environment and have access to the same data.  Plus, we'll have data redundancy and backups.    BTW, I do have read access to my ext3 partition in Windows via an L: drive....

Thanks!
KF[/QUOTE]
 I should point out that a cp -update command is not sufficient in the case that a file is deleted on the source partition....  Net, I'm guessing I need something that has some indexing capability...

---

### Post by Magneto on 2004-12-06
why not just write to the my pictures folder on the ntfs drive? that works and its not experimental anymore

---

### Post by killerfish on 2004-12-06
[QUOTE=Magneto]why not just write to the my pictures folder on the ntfs drive? that works and its not experimental anymore[/QUOTE]
 I thought it was only for same size files/etc.  Net, like if I 'touched' up a picture and file size changed it would not be able to save it back.. Plus, I couldn't delete....

Actually, I found some threads here confirm that ntfs write access is still not safe unless using captive-ntfs (I've done this, but it's SLOW)....

[http://www.ubuntuforums.org/showthread.php?t=1685&highlight=ntfs+write](http://www.ubuntuforums.org/showthread.php?t=1685&highlight=ntfs+write)

---

### Post by killerfish on 2004-12-06
[QUOTE=killerfish]I thought it was only for same size files/etc.  Net, like if I 'touched' up a picture and file size changed it would not be able to save it back.. Plus, I couldn't delete....

Actually, I found some threads here confirm that ntfs write access is still not safe unless using captive-ntfs (I've done this, but it's SLOW)....

[http://www.ubuntuforums.org/showthread.php?t=1685&highlight=ntfs+write](http://www.ubuntuforums.org/showthread.php?t=1685&highlight=ntfs+write)[/QUOTE]
 Solved Linux side....sort of.. Can't believe I didn't think of this:

rsync -r --delete /mnt/winxp/.../My\ Pictures /home/john/my_pictures

works great, but still slow considering I have > 5000 pictures...  Anyone aware of any faster programs?

---

### Post by WW on 2004-12-06
A program that I've been meaning to try myself is **unison**.  According to the description that I read in Synaptic, it runs on both *nix and Windows.  I haven't tried it yet, but it sounds like it might work for you.

---

### Post by killerfish on 2004-12-06
Unison is a great suggestion, but it seems to only be 2 way vs. 1 way synchronization... Unless I'm reading the docs wrong.. I'll double-check b/c rsync is way to slow for this many files..

Thanks!
KF

---

### Post by JsPr on 2004-12-06
Get a cheap box and use it as a server for your common files? :-)

---

### Post by killerfish on 2004-12-06
True, I could do that, but I shouldn't have to if they're on separate  drives in the same machine.  Anyway, I'm using rsync on the Linux side for just the most recent month (much faster) and unison on the windows side.  For some reason, unison on Linux pukes due to the readonly nature of an ntfs partition, but on windows it doesn't fail without first working with a readonly linux partition...

---

### Post by Magneto on 2004-12-06
a small vfat partition?   I use a 2.6.9 patched kernel and have had no issues with ntfs writing but I also have a vfat partition that I use for my music and documents so that I can do what I like with whatever on my laptop which dual boots ubuntu and xp, ive been doing things that way for a year or so now
no unallocated space? partition magic, rearrange somethings

---

### Post by regeya on 2004-12-06
[QUOTE=killerfish]I have a dual boot system.  I'd prefer Linux, my wife prefers Windows.  I'm looking for program that I can run when Linux starts that will do folder synchronization with the My Picture's folder in my windows installation.  It needs to be 1 way since my windows partition is NTFS.  

Net, here's what I'd like to do.  When Linux starts, it will find any changes I made below My Picutres on my windows partition and copy them to a my_documents folder on my Linux partition.  Then, say I download some pics in Linux to this folder.  Finally, when I reboot to windows, I'd like windows to do a similar copy from my ext3 partition...  This way, my wife and I will always be able to work in our preferred environment and have access to the same data.  Plus, we'll have data redundancy and backups.    BTW, I do have read access to my ext3 partition in Windows via an L: drive....

Thanks!

KF[/QUOTE]

I take it you're both on the same machine, so here goes: why not a FAT32 partition, as someone else suggested?  Both Windows and Linux can read/write FAT32 just fine.  Come to think of it, I'd be worried if Windows *couldn't* deal with FAT32. ;)

---

### Post by killerfish on 2004-12-07
This is true.  I could have a shared FAT32 partition.  Maybe I'll do this.  One thing I like about the way I'm currently doing is it makes for easy data redundancy.  Really, the only data I care about on my computer is my pictures of the kids.  Net, if one hard drive goes, I'm still good. 

I guess if I have a shared partition I could have a cron job that does an rsync every week to a partition on another disk....

---

### Post by nzgreen on 2004-12-10
[QUOTE=Magneto]no unallocated space? partition magic, rearrange somethings[/QUOTE]
or you could try:
```
/sbin/parted
```
There are two GUI versions available - [gparted](http://gparted.sourceforge.net/) and [qtparted](http://qtparted.sourceforge.net/).  qtparted is in universe and according to the gparted news page there's an Ubuntu package available for that.

---

### Post by jdong on 2004-12-11
The original question: **rsync -av --delete --progress source destination** performs an intelligent copy, only copying files (and parts of files) that have been changed. It also removes files that are in destination but not in source, so **BE CAREFUL** issuing the command!!!

---

### Post by Magneto on 2004-12-11
i thought i posted this earlier- THANKS  i looked for a gnu app like this last year or the year before and didnt find anything -

---

### Post by dare2dreamer on 2004-12-12
You might have a look at a program in the repositories called mirrordir, I use it all the time for all sorts of quick folder sync'ing.

---

