---
title: "What File System do you use/recommend?"
date: 2005-10-20
forum: General Help
---

### Post by Jeff Hunter on 2005-10-20
I use ReiserFS, but I want to learn more about the other options available...Linux is about choice, after all, right?

---

### Post by Grey on 2005-10-20
I use EXT3.  It's not as fast as some of the alternatives... but it's safe to use, it's mature, and stable.  And as an added bonus, there are tools to read EXT2/EXT3 drives from Windows if I really need to use Windows for something.    I am not aware of such tools for Reiser.

---

### Post by james4e on 2005-10-20
I installed breezy on ReiserFS. I used ext3 before. However, I found ReiserFS will make my computer very slow if there is a constant harddisk operation. This situation never happened on ext3 file system. I can operate my computer as usual even if there is a constant harddisk operation on ext3.

Is there anybody can verify my this situation?

---

### Post by mr_manny on 2005-10-20
ext2/3 are the default for linux = more likely to be compatible w/future releases.
I have installed development kernels/recompiled in order to recognize reiserFS.

something to think about...

---

### Post by raublekick on 2005-10-20
i've never used anything but ext2/3. I wanted to try ReiserFS with Breezy, but I didn't even think about it during the install, so ext3 it is again!

my 120 gig drive is one big FAT32 partition. As far as I know that's the only way to share a drive between both Windows and Linux (without using an extra tool as mentioned above, which I hear are not entirely stable).

---

### Post by lucas on 2005-10-20
[QUOTE=Grey]I use EXT3.  It's not as fast as some of the alternatives... but it's safe to use, it's mature, and stable.  And as an added bonus, there are tools to read EXT2/EXT3 drives from Windows if I really need to use Windows for something.    I am not aware of such tools for Reiser.[/QUOTE]

There are tools to read reiserfs from windows, but not to write or as a driver.
[rfstool](http://p-nand-q.com/download/rfstool.html) and a  [gui](http://p-nand-q.com/download/rfstool.html) for it

---

### Post by objorkum on 2005-10-20
It's ReiserFS, not RieserFS...

---

### Post by fedetxf on 2005-10-20
I have allways used the default (ext3 since the RedHat 9 era). I had power failures, kernel problems freezing the whole computer fromtime to time, etc. I never ever had a lost file. I had very few times when the filesystem check required me to recover and that recovery was merely recreating the journal because the computer had not been properly shut down. 

Now with newer ext3 versions it does not even require a filesystem check when crashing or resetting it. Ext3 makes me feel safe.

---

### Post by Einaras on 2005-10-20
I user ReiserFS, but i wanted to try XFS and JFS, but i don't no nothing about those, so maybe later :)

---

### Post by Jeff Hunter on 2005-10-20
[QUOTE=objorkum]It's ReiserFS, not RieserFS...[/QUOTE]
My apologies.  Will correct.

Can't correct the poll, but I can correct my own post.

---

### Post by SickTwist on 2005-10-20
[QUOTE=fedetxf]I have allways used the default (ext3 since the RedHat 9 era). I had power failures, kernel problems freezing the whole computer fromtime to time, etc. I never ever had a lost file. I had very few times when the filesystem check required me to recover and that recovery was merely recreating the journal because the computer had not been properly shut down. 

Now with newer ext3 versions it does not even require a filesystem check when crashing or resetting it. Ext3 makes me feel safe.[/QUOTE]

Ext3 is set to do a check after every X reboots. When the time comes for it to do a filesystem check, believe me you'll notice as it is   s----l----o----w. I'll agree with you though that it is very stable.

---

### Post by kingsidy on 2005-10-20
i use ReiserFS. That is the one Suse uses by default I think. As an ex Suse user, I went for Reiser with Ubuntu. Plus i think that it check the filesystem for error every 30 boots or so.

---

### Post by bored2k on 2005-10-20
Unless I'm mistaken, the 30 boot checks is done by EXT3.

Personally, I'm a Reiser kind of guy.

---

### Post by Mizzou_Engineer on 2005-10-20
RFStool and Yareg allow for one to read a ReiserFS partition from Windows. I know it works because I use it.

---

### Post by dave9191 on 2005-10-20
ReiserFS for me :) I used to use ext3, but I gave this a try and I love it. I don't notice any real differnces apart from the lack of the check that runs every 30 times you mount ext3. And the rapid formatting and recovery after a hard reset. 

As for being able to write to linux partions from windows... do you really want a windows virus to mess up your windows install as well as your linux install? I would not be happy letting windows write to my linux file system. 

Dave

---

### Post by dtfinch on 2005-10-20
I used to favor reiserFS, but now I stick to ext3. I might switch back to reiser4 in a couple years.

I've seen a lot of conflicting benchmarks, all of which attempt to be broad and fair. Sometimes reiser wins every test, and sometimes it loses a majority of them, both v3 and v4. Ext3 seems to be a very steady performer unless you put tens of thousands of files in the same directory, and I've seen it win more than one benchmark hands down. Sometimes this is attributed to reiser being very cpu intensive. Ext3 also has a very good record for surviving crashes and power losses. Ext3's filesystem format/layout is undoubtably inferior to the reiser filesystems, but the implementation is very stable, mature, reliable, efficient, and battle tested. So I'll stick to ext3 for now.

But I've also heard that Red Hat does a good job at making ext3 the fastest and most reliable filesystem available with their distributions by often accidentally breaking or impairing the alternatives, which could account for some of the speed and reliability benchmarks I've seen where ext3 kicks ass. Hans doesn't seem to like RH from having read some of his posts.

---

### Post by skoal on 2005-10-21
[QUOTE=dtfinch]I've seen a lot of conflicting benchmarks[...][/QUOTE]
Yes, sir! Ain't that the truth.  Everytime I run across one, I'm reminded of Chris Farley in Tommy Boy stumbling over his first sales pitch, 

"*Hey, I'll tell you what. You can get a good look at a butcher's ass by sticking your head up there. But, wouldn't you rather take his word for it*?"

I've actually stuck my head in the code and seen many a benchmark too. Not much light in there, and they all stink (the benchmarks that is).  In the end, the guy (and his benchmark) really are butchers, in every sense of the word.

ext3 or reiserfs stability? Guarantees of it? That one's equally tackled by Tommy Boy,

"*Hey, if you want me to take a dump in a box and mark it guaranteed, I will. I got spare time.*"

...

I won't butcher anything here, but only give a few sticking points based on experience.  First, I love reiserfs.  In a nutshell, I find it faster on searching huge (and I mean huge!) sets of files (in the order of hundreds to thousands).  However, something as simple as opening a single file has a slight lag compared to ext3.  I personally find reiserfs a litte more robust (ok, stable, I'll use that term) on unexpected crashes and subsequent reboots.  I don't run to the bathroom and clip my nails or shave while waiting for fsck.ext3 to finish anymore.  One other big caveat with reiserfs is the fixed journal size of 32MB, where ext3's is dynamic.  Reiserfs chews up precious precious hdd real estate, like on my 64MB /boot and 128 MB /home partition because of it.  Oh well, small gripe and I'm too lazy to really care or change those sizes at this point.

By the way, I've followed 'ole Reiser himself on the lkml, and agree with most of his technical arguments.  I never really heard he had some beef with the RedHat guys, but that would make sense I guess.  Wasn't Stephen Tweedie working for RedHat at the time when he made ext3 (by journaling ext2)?  Seems like him and other devs stole some of Reiser's thunder awhile back, and that humble pie dish him and others on lkml are eating from seems rather empty these days, IMHPO (the 'P' is for pie! mmmm...sweet sweet juicy humble pie...).  

\\//_

---

### Post by hajk on 2005-10-21
A large ReiserFS for mounting my root (/) partition, and a small bootable (50MB) ext2 partition for /boot -- not taking any chances there!:razz:

---

### Post by asimon on 2005-10-21
In my experience reiserfs is not less stable or reliable then ext3. Thus I use reiserfs because it's the fastest fs for my use cases. I made some tests with reiser4 and plan to switch when it's more mature (probably somewhen next year).

For /boot I use ext3 because I usually have rather small /boot partitions and reiserfs eats 32MB away for it's journal, which isn't worthwhile anyway for /boot.

Besides from this I use LVM or EVMS everywhere I can.

---

### Post by yage on 2005-10-21
Been using XFS for some time now and i'm very happy with it... 
My / partition is ext3 and i don't know why... has been that way for ages! XFS is fast and stable and no fsck needed :)

---

### Post by dtessier on 2005-10-21
[QUOTE=asimon]In my experience reiserfs is not less stable or reliable then ext3. Thus I use reiserfs because it's the fastest fs for my use cases. I made some tests with reiser4 and plan to switch when it's more mature (probably somewhen next year).

For /boot I use ext3 because I usually have rather small /boot partitions and reiserfs eats 32MB away for it's journal, which isn't worthwhile anyway for /boot.

Besides from this I use LVM or EVMS everywhere I can.[/QUOTE]

For /boot, which in theory is not written to very often, ext2 is sufficient. No journalling is really required there.

---

### Post by hachre on 2005-10-21
I've been using reiserfs3 for well over 4-5 years now.
I've never ever had problems with it.

My own tests showed that using reiserfs the fs could always recover when killing power while writing to the drive.
Ext2 and 3 sometimes failed to recover and there was nothing I could do to get it back working...

---

