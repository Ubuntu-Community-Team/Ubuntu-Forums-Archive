---
title: "Copy data to drive says there is not enough space."
date: 2013-12-20
forum: General Help
---

### Post by roberttheed on 2013-12-20
Ok, I know this sounds like a total noob question but this is like the 8th roadblock I have hit in what should be a simple process of copying data from one drive to another. Just so no one thinks I am an idiot, I have a career in IT security, been doing this for many years, blah, blah, blah. Anyway, I have two 2TB drive. One formatted in reiserfs with 63gb free. The other is empty, freshly formatted in NTFS. I have made sure several times, formated it in Windows and Ubuntu. The entire available space is being used for the partition. However when I copy the data from the reiser disk to the NTFS disk I get a message that I need 5.2 more GB and for the life of me have no idea what is going on. I was using GNOME Ubunutu x64 13.10 but I tried it on Ubuntu x64 12.04 as well and get the same things. What is going on? The only thing I can think of that could *possibly* cause it is a symlink but I almost certain I have never done one on it. I don't even know how I would check that. I have never been this confused about IT in my life.

---

### Post by TheFu on 2013-12-20
IT security with Windows doesn't transfer to Linux very much.
How are each drives mounted? Are you using kernel drivers or FUSE?  Is the NTFS on a Windows PC over the network?  Doesn't Windows require every network copy file to be stored in a temp dir on C:? Is there enough space there?

Are you trying to drag-n-drop the files or using CLI?  From the shell, things like errors are usually easier to see and understand.

What do the log files on the system failing say?

Just shots in the dark.

---

### Post by roberttheed on 2013-12-20
I work IT security in Windows and Linux. I wouldn't say I am an expert with Linux but I have been using it for many years and use it almost on a daily basis. I know my way around about a half dozen different distros.

Anyway the resier disk is from my NAS and the NTFS is a spare. No networking, just swapped the hardware in, loaded the vanilla Ubuntu iso from a live usb, opened the the folder with whatever the default file explorer is, selected the two folders, right click, copy, go to other drive, right click paste. This is just from the live ubuntu iso.

---

### Post by TheFu on 2013-12-20
Can you please try the copy without any GUI?  I bet it will work.

---

### Post by roberttheed on 2013-12-20
i was going to try that and i am now. i just didnt want to wait for the 8+ hours it takes to copy only to find out it didn't work.

---

### Post by TheFu on 2013-12-20
For things that take long times to top, I use rsync.

Greatest discoveries of man:
* fire
* wheel
* unix
* ssh 
* rsync !
* germ theory / vaccines

Is this 1 file?  Could it be that NTFS has a filesize limit that is being hit?  Or perhaps the FUSE NTFS driver being used?  I'm confident that the log files would have errors/warnings from the prior failures that would be helpful.

root or some other user?  Is the NTFS partition mounted with the user that is doing the copy as "owner"?

Just shooting in the dark at this point.

---

### Post by Bashing-om on 2013-12-20
roberttheed;
Another shot in the dark .. reserved space.
Ext4 reserves 5 % by default; How about that overhead space differences for resier and NTFS ? I have not done the arithmetic but 63 gigs in 2 TB is not that much, percentage wise (??) .

[INDENT][INDENT]just a thought
[/INDENT][/INDENT]

---

### Post by roberttheed on 2013-12-20
> **Bashing-om said:**
> roberttheed;
Another shot in the dark .. reserved space.
Ext4 reserves 5 % by default; How about that overhead space differences for resier and NTFS ? I have not done the arithmetic but 63 gigs in 2 TB is not that much, percentage wise (??) .
[INDENT][INDENT]just a thought
[/INDENT]
[/INDENT]


i thought about that too but 63gb+5gb seemed a lot too me. maybe not. but i would imagine ubuntu would adjust the reported size for the overhead. they both report 2tb.

---

### Post by roberttheed on 2013-12-20
> **TheFu said:**
> For things that take long times to top, I use rsync.

Greatest discoveries of man:
* fire
* wheel
* unix
* ssh 
* rsync !
* germ theory / vaccines

Is this 1 file?  Could it be that NTFS has a filesize limit that is being hit?  Or perhaps the FUSE NTFS driver being used?  I'm confident that the log files would have errors/warnings from the prior failures that would be helpful.

root or some other user?  Is the NTFS partition mounted with the user that is doing the copy as "owner"?

Just shooting in the dark at this point.

its a little over 4k files. i dont image the drive would be in use as that is the only task i have done since booting up. i'll check the logs if this copy fails.

i already chowned the files.

---

### Post by oldfred on 2013-12-21
You do know that with NTFS you lose all permissions & ownership. NTFS does not support those. If just data files it will not matter, but if system files or executables then it may matter a lot.

I think you are so close in size that the type of formatting does make a difference. Also is new drive a 4K drive and old one not a 4K drive? That also may make some difference.

[http://en.wikipedia.org/wiki/ReiserFS](http://en.wikipedia.org/wiki/ReiserFS)
As I read it, you may have some small files packed which in NTFS would all be separate.

---

### Post by roberttheed on 2013-12-21
> **oldfred said:**
> You do know that with NTFS you lose all permissions & ownership. NTFS does not support those. If just data files it will not matter, but if system files or executables then it may matter a lot.

I think you are so close in size that the type of formatting does make a difference. Also is new drive a 4K drive and old one not a 4K drive? That also may make some difference.

[http://en.wikipedia.org/wiki/ReiserFS](http://en.wikipedia.org/wiki/ReiserFS)
As I read it, you may have some small files packed which in NTFS would all be separate.

yes, i know, it is just an archive from my NAS, no system files. i am starting to think it is a discrepancy between file systems. it just seems like a big one to me. i'll see if this transfer yields any errors. the reiser with the data is a wd caviar black and the blank ntfs is a wd green. the wd green is 4k.

---

### Post by TheFu on 2013-12-21
> **roberttheed said:**
> its a little over 4k files. i dont image the drive would be in use as that is the only task i have done since booting up. i'll check the logs if this copy fails.

i already chowned the files.

Fresh day. Re-read the OP and have a few ideas.
[LIST=1]
[*]How are each mounted?  FUSE, kernel, gvfs?
[*]Is the source drive completely full?  Output from **df -kh** please.
[*]Assuming a full source drive, we need to know the overhead of NTFS formatting. Could it take more space than ReiserFS?  Only matters if the source is full.
[/LIST]

OTOH, did rsync work last night? We really want to know!

---

### Post by roberttheed on 2013-12-21
> **TheFu said:**
> Fresh day. Re-read the OP and have a few ideas.
[LIST=1]
[*]How are each mounted?  FUSE, kernel, gvfs? 
[*]Is the source drive completely full?  Output from **df -kh** please. 
[*]Assuming a full source drive, we need to know the overhead of NTFS formatting. Could it take more space than ReiserFS?  Only matters if the source is full. 
[/LIST]

OTOH, did rsync work last night? We really want to know!

most of that is in the OP.
they are mounted however ubuntu mounts them automatically on startup.
the source drive has 63gb free.
i used cp to copy and it worked fine, although there is a small discrepancy in freespace. the source drive says there is 63.2gb free and the target says 64.9.

here is the output of df -kh after the copy:

Filesystem      Size  Used Avail Use% Mounted on
/cow            2.0G  697M  1.3G  36% /
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           791M  968K  790M   1% /run
/dev/sda1       3.8G  708M  3.2G  19% /cdrom
/dev/loop0      667M  667M     0 100% /rofs
tmpfs           2.0G   92K  2.0G   1% /tmp
none            5.0M  4.0K  5.0M   1% /run/lock
none            2.0G  148K  2.0G   1% /run/shm
/dev/sdc1       1.9T  1.8T   59G  97% /media/da32d6d3-cf2a-4693-b3f6-5f30a289b1ca
/dev/sdb1       1.9T  1.8T   61G  97% /media/36256CCD54BD8C5D

---

### Post by TheFu on 2013-12-21
Looks like file system differences to me.  You could run an md5sum against every file on each file system and compare the outputs if you needed to be almost positive no changes in the data exists.
Using **find | wc** is another way to get a close-enough answer if you just want to know that the files were copied.

There are also duplicate-finding tools like **fdupes** that should work faster - just point them to /media.  Hopefully, every file will have a dup.

---

### Post by roberttheed on 2013-12-30
ok, i got the data copied over on all my drives. i verified in ubuntu that the copy worked and opened a bunch of files. files loaded file, partitions looked good. however, when i put the drives into a windows machines it cannot recognize the partition. i put them back into ubuntu and it also cannot recognize them. so i got some partition recovery tools and recopied everything again and formatted the drives within windows. it took an additional week because of this. i no longer trust the ntfs driver that ubuntu uses.

oddly, one drive that was formatted in ubuntu did read in windows but oddly enough, i had the same issue as before but on windows. i tried to copy the 2tb drive (63gb free) to another empty 2tb drive and it said i needed 5gb more space. however i think i got that part figured out.

it seems by default ubuntu uses compression. in windows it did not and when i looked at the properties of another drive in windows it has the option to compress drive to save space. on the linux drive the option wasnt there. when i checked the capacity on the windows formatted ntfs drive the size and size on disk matched up. in the linux formatted ntfs drive the size was greater than size on disk.

so i believe that was the cause of my original problem. no clue as to why all but one of the 13 partitions was unreadable once installed into a windows machine though. i should have gone with my gut and used windows to format them in ntfs instead of linux but i was lazy and didnt want to add extra steps and have it take longer. in the long run it look about a week longer anyway since i had to redo everything.

---

