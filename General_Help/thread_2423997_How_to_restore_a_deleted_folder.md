---
title: "How to restore a deleted folder?"
date: 2019-08-01
forum: General Help
---

### Post by peyre on 2019-08-01
Yow!  I aborted a copy operation this morning, then went to delete the directory I had partly copied to flash drive - except instead I shift-deleted the directory **from the hard drive!!**   ](*,)

My own fault, I know, but I would really like to recover certain files from that directory.

I've installed **testdisk**, but when I select that folder and copy it to another location, it copies it as an XML file instead.  When I have the folder name highlighted and I hit Enter or right arrow, it doesn't open the folder to see its contents.  Any ideas?  The tutorials I've found for testdisk seem to imply I can open the folder or copy it out, but it's just not working for me.

(This is a mechanical hard drive, not an SSD, if that matters.)

---

### Post by #&amp;thj^% on 2019-08-01
TestDisk has been a very valuable tool for my self along with:
recoverjpeg: [https://rfc1149.net/devel/recoverjpeg.html](https://rfc1149.net/devel/recoverjpeg.html)
Should be in the Repos.
Good luck though.
BTW I've never seen an XML using TestDisk that I can remember anyway

---

### Post by peyre on 2019-08-01
The files I'd particularly like to recover are .mp4, not .jpg or .mov, so I don't think recoverjpeg would be much help in my case.

Testdisk, yes, would be great, but it doesn't seem to want to cooperate on this one, as mentioned.  *Unless*, of course, I'm missing something - which I hope is the case.  I'm brand spanking new to testdisk.

---

### Post by #&amp;thj^% on 2019-08-01
> **peyre said:**
> The files I'd particularly like to recover are .mp4, not .jpg or .mov, so I don't think recoverjpeg would be much help in my case.



Don't let the name fool you, it also recovers partitions, files, etc, etc. and has worked when TestDisk just wasn't up to the task.
recoverjpeg currently restores over 200 different filetypes, not just .jpegs)
More Info for TestDisk: [https://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](https://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by peyre on 2019-08-01
So frustrating.

Ok, so I've installed recoverjpeg though Synaptic, but now when I run it it says nothing's there.  I run:
```
sudo recoverjpeg "/home/leon/Storage/Graphics/Movies/Lord of the Rings/Hobbit Purist Mod/Hobbit2/White Council.mp4"
```
and it says "recoverjpeg: unable to open /home/leon/Storage/Graphics/Movies/Lord of the Rings/Hobbit Purist Mod/Hobbit2/White Council.mp4 for reading (No such file or directory)".

If I enter the path to the folder that was deleted, Hobbit2:
```
sudo recoverjpeg "/home/leon/Storage/Graphics/Movies/Lord of the Rings/Hobbit Purist Mod/Hobbit2"
```
it returns "recoverjpeg: unable to open /home/leon/Storage/Graphics/Movies/Lord of the Rings/Hobbit Purist Mod/Hobbit2 for reading (No such file or directory)". Same error, basically.

I have nothing open besides Terminal Emulator and Thunar.

---

### Post by #&amp;thj^% on 2019-08-01
Is "Storage" the original Disk where the file was whole, or is it the the partial copied device?
BTW How long did you let the copy/move go before you aborted?

---

### Post by peyre on 2019-08-01
Ah, good question.  This is a project whose files I copied over from another computer, and I wanted to mimic the file structure.  So I created the Storage folder in my home directory on this machine.

On my desktop machine, my mechanical drive is mounted as Storage.  But on this machine, it's just a folder in my home directory.

(The reason for all this shuffling around was that I'm doing some video editing, and that was becoming awfully slow on my desktop computer, so I borrowed a laptop from work with more and faster processors.)

---

### Post by #&amp;thj^% on 2019-08-01
So if i understand correctly, the Original video was on>>>"the mechanical drive is mounted as Storage".
If so was TestDisk pointed to that? I think you get my thought or point here.
BTW: Don't give up just yet, I've also had very good results booting to a live environment with TestDisk installed.
I've only experienced failure with both tools mentioned less than 5 times under severe conditions. (Formatted Over)

---

### Post by peyre on 2019-08-01
No.  The old desktop computer and its mechanical drive aren't involved at this point.  I copied the files from there to this laptop.  Then I did several evenings' work on the laptop, then accidentally deleted it all on the laptop.  The original files I copied are still on the old desktop, unchanged from that point.

TestDisk (and recoverjpeg) are being pointed to the folder on the laptop.  Right now the desktop (with the mechanical drive mounted as "Storage") isn't even on.

---

### Post by #&amp;thj^% on 2019-08-01
I must be dense here, and I'm not trying to be a hard case here, I have a real concern for those that have lost data of any kind. (Been There Myself, and lesson learned) 
> **peyre said:**
> No.  The old desktop computer and its mechanical drive aren't involved at this point.  I copied the files from there to this laptop.
The original files I copied are still on the old desktop, unchanged from that point.
  
So there is a back-up of each then?

---

### Post by peyre on 2019-08-01
Um.  Unless Xubuntu has an equivalent of Windows' Previous Versions, no.  Just to reiterate, what happened was:
1. Original files created on desktop computer (I still have these)
2. Original files then copied to laptop
3. Work done on files copied to laptop
4. Files on laptop deleted.

I perform backups on my desktop, but haven't been backing up this other machine because it's a temporary situation.  So there are backups of the old files on my desktop, but not of the laptop, where most of the work was done.

---

### Post by #&amp;thj^% on 2019-08-01
> **peyre said:**
> 
I perform backups on my desktop, but haven't been backing up this other machine because it's a temporary situation.  So there are backups of the old files on my desktop, but not of the laptop, where most of the work was done.
Yep I knew/thought you would be the user-type to have back-ups. I've been around here for over a decade, and kind of have a feel for most of the Old-Timers if you will. :)
> **peyre said:**
> Just to reiterate, what happened was:
1. Original files created on desktop computer (I still have these)
2. Original files then copied to laptop
3. Work done on files copied to laptop
4. Files on laptop deleted.
.
I can only see at this point the worst case, would be the work done lost.
I just copied a video over to a test file on a different Drive then used Shift Delete on the copied file, TestDisk was able to restore the file.
I'm off to work now, but only a short shift tonite so I'll check back hoping for a success here. ;)

---

### Post by peyre on 2019-08-01
> **1fallen said:**
> Yep I knew/thought you would be the user-type to have back-ups. I've been around here for over a decade, and kind of have a feel for most of the Old-Timers if you will. :)
Thank you, that's very kind!  I do IT for a living, so I'm very conscious of the importance backups (as users go - I occasionally neglect them here or there and tempt fate, as I seem to have here).

> **1fallen said:**
> I can only see at this point the worst case, would be the work done lost.
I just copied a video over to a test file on a different Drive then used Shift Delete on the copied file, TestDisk was able to restore the file.
I'm off to work now, but only a short shift tonite so I'll check back hoping for a success here. ;)
Thanks, I would be glad to see you check in again later.  I hope I can work something out; these files represent maybe a dozen hours of evening time spent, and my evening hours are in rather short supply.  Between work, a long commute, and family obligations, my evening doesn't start until 8pm, and bedtime's at 10.

---

### Post by peyre on 2019-08-01
Ah, hm, I think there may be some trouble with the file system, or maybe some key file has been overwritten or corrupted.  I tried extundelete while booted from a Xubuntu DVD:
```
sudo extundelete --restore-file "/home/leon/Storage/Graphics/Movies/Lord of the Rings/Hobbit Purist Mod/Hobbit2" /dev/sda1
NOTICE: Extended attributes are not restored.
Loading filesystem metadata ... 3727 groups loaded.
Loading journal descriptors ... 0 descriptors loaded.
extundelete: Extent block checksum does not match extent block while finding inode for Hobbit2
extundelete: Extent block checksum does not match extent block while finding inode for Hobbit2
Failed to restore file /home/leon/Storage/Graphics/Movies/Lord of the Rings/Hobbit Purist Mod/Hobbit2
Could not find correct inode number past inode 24773130.
Try altering the filename to one of the entries listed below.
File name                                       | Inode number | Deleted status
extundelete: Operation not permitted while restoring file.
extundelete: Operation not permitted when trying to examine filesystem
```

I received similar results when including the name of a specific file to be undeleted.

---

### Post by #&amp;thj^% on 2019-08-01
This just baffles me, I followed your procedure, {IE:} Aborted a copy (cp) to a folder on my main drive from another drive, then ran TestDisk and now get the same message you are seeing.
But I remembered another nifty little tool "debugfs", Now this works only on a "ext3" format, but I like playing around.
I gave it go and had what i thought was going to be a winner, but sadly it still failed.
If you want or still can with the borrowed Laptop, give this a whirl.
Found here: [https://www.cyberciti.biz/tips/linux-ext3-ext4-deleted-files-recovery-howto.html](https://www.cyberciti.biz/tips/linux-ext3-ext4-deleted-files-recovery-howto.html)

---

### Post by dragonfly41 on 2019-08-02
Another experiment to try for file recovery is R-Linux.

From their help intro ..

[COLOR=#000000][FONT=Arial]**R-Linux** is a file recover utility for the Ext2/3/4FS file system used in the Linux OS and several Unixes. **R-Linux** uses unique **IntelligentScan** technology and flexible parameter settings to give you real control over the fastest data recovery ever seen. It recovers files from existing partitions even when file records are lost.[/FONT][/COLOR][COLOR=#000000][FONT=Arial]**R-Linux** is a lite version of more powerful file recover utility **R-Studio**. **R-Studio** utilizes the IntelligentScan technology to its full extent, and therefore can recover data from partitions with broken file systems. Also, **R-Studio** recovers data over network. To learn more about **R-Studio**, go to the **[R-Studio Features]("https://ubuntuforums.org/r-studiofeat.html")** help page. To learn more about the **IntelligentScan** technology, go to the **IntelligentScan** help page.


[/FONT][/COLOR]

---

### Post by mastablasta on 2019-08-02
this could be the case where file systems such as BTRFS or ZFS might come in handy. just throwing it out there.

also i think ubuntu should have the undelete option that MS has had since DOS.

---

### Post by dragonfly41 on 2019-08-02
Studying again the extundelete error report in post #14 I found this ...

[https://unix.stackexchange.com/questions/454536/extundelete-how-to-solve-block-bitmap-checksum-does-not-match-bitmap-when-try](https://unix.stackexchange.com/questions/454536/extundelete-how-to-solve-block-bitmap-checksum-does-not-match-bitmap-when-try)

and
[https://sourceforge.net/p/extundelete/mailman/message/25798145/](https://sourceforge.net/p/extundelete/mailman/message/25798145/)

---

### Post by #&amp;thj^% on 2019-08-02
extundelete still results in failure on my end, with options used "--restore-inode" and "all"
again was teased with "--restore-directory" but still reports, **"Could not find correct inode number past inode xxx"** I added the xxx for example only.
However with combination of debugfs And R-Linux I finally got it to work, but size was greatly reduced to about 15% of the original size and quality was not great, so not quite there yet.
Still working on this though. (I'm a moth drawn to flame with this now :D) 
BTW: Thanks to dragonfly41 for the mention of **R-Linux** I'd never even heard of it before this. This tool is a keeper! ;)

---

### Post by peyre on 2019-08-02
That's great, 1fallen!  I've made a clonezilla image of the drive and will start trying things gain.

Mastablasta, I'm with you 100% that *buntu is *long* overdue for a built-in undelete feature.

---

### Post by Skaperen on 2019-08-02
so, it is the several evenings of work on copies of all these files you want to recover.  when the accident happened, did you do a sudden power off (or "halt -f") or did you do a clean, graceful shutdown?  or did you just spend time looking around for some quick way to recover from this oops?

my concern is that the metadata, the inodes and data block locations for these files is gone.  if you wrote any file data (new files, appended old files, etc) anywhere on the filesystem where those files were, then some or all of the data blocks may also be gone (written over).  a program that can look at the partition's raw sectors and discover "loose data" and understands how to piece the the block back together in the right order is what you need, if the data is still there.

such a program is plausible for images and videos.  the start of such files is fairly well known.  then, by understanding the format, it can select candidate block that come next that fit that point in the format and decode the image or video well into that block.  then it would evaluate how consistent the imaging and framing is to judge which block is best to follow.  this would be repeated and it would end up with a bunch of unnamed (probably numbered) files.

if the many evening's work was renaming files and arranging them into subdirectories, i'm very sure that kind of work is hopelessly gone.  since you do have original copies, if you did not alter any data, those copies are your best bet.  if you cannot recover anything, thenthis lesson should stick with you for quite a while.

please note that about 35 years ago i personally made a much greater oops.

---

### Post by peyre on 2019-08-02
Once I realized what I had done (and looked around to make sure), I did a graceful shutdown.  I've since booted it only to try to recover data, and copy off the files that haven't been deleted.  But several pieces of advice here have had me install programs to try to undelete the files, so that may have overwritten those things you mentioned.

---

### Post by #&amp;thj^% on 2019-08-02
The only thing needed on my end was R-Linux, debugfs should be installed. (I think anyway)

---

### Post by dragonfly41 on 2019-08-02
> [COLOR=#000000]But several pieces of advice here have had me install programs to try to undelete the files, so that may have overwritten those things you mentioned.[/COLOR]

You are probably right. A piece of advice which perhaps should have been given (too late now) is that the drive where the files are deleted should be frozen, not used, and preferably cloned using dd so that you have a cloned device to work on for recovery.  Next you have a LiveUSB where recovery tools such as testdisk, R-Linux, and others can be safely run.  Finally if you have many files to recover you should have another drive into which you can save any recovered files. If this workflow is not followed you stand the risk of overwriting the files you are hoping to recover.

---

### Post by #&amp;thj^% on 2019-08-02
Clonezilla uses "dd" but I've never used it, just "dd" for me.
BTW That advice was in the links provided. Sometimes frustration rules our thoughts. :(
And the fact that the Laptop was on borrowed time.

---

### Post by peyre on 2019-08-02
Da*n, after looking at how technical debugfs is ([http://www.tutorialspoint.com/unix_commands/debugfs.htm](http://www.tutorialspoint.com/unix_commands/debugfs.htm)), I think it'd be easier to just redo all my work than to try to work that out (and all that for a "maybe" in terms of success).  Why in the world is undeleting such a nightmare on a modern, user-friendly system like Ubuntu?

---

### Post by HermanAB on 2019-08-04
The desktop GUI utilities do maintain a trashcan.  If you used the GUI file manager to delete the folder, then the data would still be there, but if you used the command line, then not.  The assumption is that people who use the command line, are supposed to know what they are doing and will make regular backups.

The other problem is that as soon as file nodes are freed, then can be used again.  So if you keep running the system and install new software, then the old data can be overwritten and then it is truly gone.  Testdisk is best run off the Ubuntu install disc, not while booted off the problem HDD.

---

### Post by peyre on 2019-08-05
Trust me, if it were in the Trash I wouldn't have posted.  I was in the GUI, but I shift-deleted, which bypasses the Trash.  (Which, btw, is a habit I should probably get out of.)

---

