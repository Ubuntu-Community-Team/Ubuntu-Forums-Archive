---
title: "Broken partition ext4 (and errors with superblock or partition table)"
date: 2014-09-28
forum: General Help
---

### Post by mikkojrh on 2014-09-28
Hi! I had a 2TB disc with three partitions in the following order:

1: 150gb ext4 partition where i store my photos
2: 850gb CRYPT-LUKS partition. I wanted to get rid of this partition.
3. 1000gb another CRYP-LUKS. 

I deleted the second one (850gb crypt-luks) with GParted. Nothing special here.

Later on i noticed i couldnt mount my photos partition, and GParted couldnt fix it becouse "either the superblock or the partition table is likely to be corrupt". After googling i found several topics about this, and decided to use command "sudo mke2fs -S /dev/sdc1 && sudo fsck /dev/sdc1". It started to ask a silly amount of questions, and i needed to terminate it since a) i were too scared to asver to them lol, and b) it seemed like there were no end for the questions. Apparently using the command was a mistake.

I were pretty helpless, but decided to try for GParted again, maybe it could fix it now. I tried to copy the partition. Now it have been running "e2fsck -f -y -v /dev/sdc1" for ~16 hours now, and its taking quite a lot memory and CPU. Is it really fixing it or is it just messing things up more? What happens if I cancel it?

And becouse someone asks it anyway: I have a backup, but it dont contain all of the photos, so thats why i want to save this partition. Well, at least the files inside it. Thanks for anyone who decides to use some time for helping.

---

### Post by oldfred on 2014-09-28
It is my understanding that you must be sure to use correct block size if using mke2fs -S command.

See post #49
[http://ubuntuforums.org/showthread.php?t=1681972&page=5](http://ubuntuforums.org/showthread.php?t=1681972&page=5)

Did you just run the e2fsck commands first. they normally are the first choice.

Not sure now but you may be able to run photorec. It also takes a very long time, and will need lots of space on another drive to copy data to. It only recovers file extension, not full filename, but photos have internal data that you can use to rename them with.

       Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

 Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)

---

### Post by mikkojrh on 2014-09-28
Hmm. GParted finished its job. Took longer than a day, and when i tried to save session information, it took more than 6gb of ram and crashed after several hours :P

I mounted the partition in read-only (just in case) and it has nothing inside of it except lost+found folder, darn it. Then i noticed that the partition was half full; lost+found folder contained thousands and thoudands of odd numeric files. I used this guide to rescue some of the files: [http://rolandeckert.com/notes/recovery](http://rolandeckert.com/notes/recovery)

Now i have 35Gb of pictures in a single folder: 13 600 files :D. However the lost+found folder is nearly twice as big, [SIZE=1][COLOR=#d3d3d3]60Gb[/COLOR][/SIZE] 80Gb. Not satisfied. Does the folders take up any space? I suppose not much..

Well but anyway next ill try your suggestion oldfred. And no, i didnt use e2fsck, but GParted might have tried it when i wanted it to fix the broken filesystem. It didnt do anything becouse superblock or partition table were corrupted. Thx for the help!

---

### Post by mikkojrh on 2014-09-29
Ahh I love you. 30 000 files saved. However many of them seems to be suplicates, only with smaller size. But maybe i had them this way before, dunno. The size of the save folder is 65Gb. I actually lied earlier, the actual size of lost+found folder is maybe about 80Gb. Sorry.

Is there any way to store the lost+found folder into another partition? I would like to delete this corrupted partition. Every time when e2fsck starts to check for errors, it takes the same time as before: about one day. Or is it useless to copy the whole folder? Is there any way to rescue more files from there? Many questions. When I try to copy the lost+found folder, it says we need an extra 2,4Tb of space to do that..

---

### Post by oldfred on 2014-09-29
If they are photos you should be able to use the meta-data that is inside the photo to rename it.

When I ran photorec it also recovered deleted files, and partial files. Since I was recovering text files that I save almost daily (my notes on what works from here) I had to find a file and compare it to last backup and see if it had new data. And some files had many copies.

I do not understand why it would want 2.4TB, but that does seem to say there is still issues & that is why it wants to re-run fsck. It may be one file is linked to another and that loops back to the original in a loop creating more files than there really are.

---

### Post by dragonfly41 on 2014-09-29
> "either the superblock or the partition table is likely to be corrupt".

Have you tried one of the backup superblock numbers?

[http://unix.stackexchange.com/questions/33284/recovering-ext4-superblocks](http://unix.stackexchange.com/questions/33284/recovering-ext4-superblocks)

---

### Post by mikkojrh on 2014-10-07
> **oldfred said:**
> I do not understand why it would want 2.4TB, but that does seem to say there is still issues & that is why it wants to re-run fsck. It may be one file is linked to another and that loops back to the original in a loop creating more files than there really are.
Maybe. I tried to ignore the size requirement and started copying the folder to another partition where were more than 500 Gb free space. It filled up.
> **dragonfly41 said:**
> Have you tried one of the backup superblock numbers?
Tried it yesterday, didn't work. I guess I should have done it before any other commands.

I suppose no one is going to post any other advice, so I will mark this thread as solved (+ I think there is nothing else I can do). Thanks for help!

---

