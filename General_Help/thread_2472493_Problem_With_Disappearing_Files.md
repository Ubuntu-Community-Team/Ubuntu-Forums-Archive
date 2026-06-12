---
title: "Problem With Disappearing Files"
date: 2022-02-28
forum: General Help
---

### Post by shane_faulkinbury2 on 2022-02-28
I'm using Ubuntu 20.04.4 LTS and I'm having a problem with video files on my external HDD.  When I first write the OS to my HDD the files show on the drive.  However, when I put the drive on my computer the second time the disappear.  When I look at my Video folder on the drive it says "Folder is Empty", but they are on it.  Windows 10 says I do not have access.

Any ideas on how to see them again on Ubuntu?

---

### Post by GhX6GZMB on 2022-02-28
> **shane_faulkinbury2 said:**
> When I first write the OS to my HDD the files show on the drive.  However, when I put the drive on my computer the second time the disappear. 
Could you rephrase this, please? I don't understand a word.

---

### Post by shane_faulkinbury2 on 2022-02-28
Okay, I first write my OS.  Then I want to install my video files on it.  I have like 5 GB.  So I hookup the external drive for the first time to my computer and see the files fine.  There are various files such as mkv, mp4, avi and so on.  I do not finish so I attach the drive at a later time.  The 2nd time and after the files do not show now.  This only happens to the video files.  Not music, documents or pictures.

---

### Post by ajgreeny on 2022-02-28
To what filesystem is the external drive formatted, ntfs,  fat32, or one of the Linux filesysyems such as ext4?
Are you certain that you unmounted the disk before removing it from the computer?

---

### Post by shane_faulkinbury2 on 2022-02-28
It's formatted to fat32 so I can use it on Windows 10 also.  Yes, I unmount it.

---

### Post by ajgreeny on 2022-02-28
How large are the video files?  Fat32 has a file size limit of 4G so large video files could be a oroblem, though I admit I would expect an error to show when trying to copy files that are too big for the filesystem.

---

### Post by Impavidus on 2022-02-28
To share files between Windows and Ubuntu you're not limited to fat32. Ubuntu handles ntfs well enough.

---

### Post by GhX6GZMB on 2022-02-28
> **shane_faulkinbury2 said:**
> Okay, I first write my OS.

I still don't understand. What does this sentence mean?

Are you trying to say that you _start/boot_ your OS?

---

### Post by shane_faulkinbury2 on 2022-02-28
No, install.

---

### Post by #&amp;thj^% on 2022-02-28
> **Impavidus said:**
>  Ubuntu handles ntfs well enough.

+1 
Now days if your sharing between windows and linux NTFS works a treat

---

### Post by GhX6GZMB on 2022-02-28
> **shane_faulkinbury2 said:**
> No, install.

So you install Ubuntu.
And when you reboot/restart your machine, it boots as Ubuntu? Sorry, but your "stenography-style" of posting gives very little information.

---

### Post by shane_faulkinbury2 on 2022-02-28
I'll reformat it NTFS which might help in Windows, but still need an Ubuntu resolution.

---

### Post by shane_faulkinbury2 on 2022-02-28
Yes and that is when I can see the video files.  After I reboot I cannot see them then or thereafter.

---

### Post by #&amp;thj^% on 2022-02-28
> **shane_faulkinbury2 said:**
> I'll reformat it NTFS which might help in Windows, but still need an Ubuntu resolution.

shane_faulkinbury2 what resolution would you need?
As ajgreeny mentioned Fat32 has a file size limit of 4G so large files of any kind won't work in a transfer. Just to be sure make sure to Install ntfs-3g and fuse on your Buntu system.
I'm totally lost here.

---

### Post by #&amp;thj^% on 2022-02-28
> **shane_faulkinbury2 said:**
> Yes and that is when I can see the video files.  After I reboot I cannot see them then or thereafter.

If they were there on boot, and after a reboot gonzo, well Huston we have problem>>I'm going out on a limb, but guessing hardware USB port, cable, and or Storage Drive it's self.

---

### Post by shane_faulkinbury2 on 2022-02-28
It could be the external since it's a 4 year old Seagate 2 TB portable expansion.  One problem I have is reformatting it.  Since I can't see the video files I can't copy/paste them.  Therefore they'd be lost.  Unless I find a computer that could see them.

---

### Post by #&amp;thj^% on 2022-02-28
> **shane_faulkinbury2 said:**
> Yes and that is when I can see the video files.  After I reboot I cannot see them then or thereafter.

> **shane_faulkinbury2 said:**
> It could be the external since it's a 4 year old Seagate 2 TB portable expansion.  One problem I have is reformatting it.  Since I can't see the video files I can't copy/paste them.  Therefore they'd be lost.  Unless I find a computer that could see them.
Do me a favor if you would, shutdown Ubuntu when off>> unplug the storage/drive, now with it still not plugged in>>>power up Ubuntu when your logged in and everything has simmered down, now plug your drive back in. Anything?

---

### Post by shane_faulkinbury2 on 2022-02-28
No go!

---

### Post by #&amp;thj^% on 2022-02-28
Well it dose see the drive, Was your files in Folders, or just the videos.mkv,avi,mp4, I think you know what I mean right? ;)
**EDIT:**While you can still see the drive, might not hurt now to see if testdisk can find and move them elsewhere.

---

### Post by shane_faulkinbury2 on 2022-02-28
Good idea on the test disk.  Wish I had a before and after though.  Yes, there are about 10 folders on the drive.  I can see them all except the files in the Videos folder.

---

### Post by #&amp;thj^% on 2022-02-28
> **shane_faulkinbury2 said:**
> Good idea on the test disk.  Wish I had a before and after though.  Yes, there are about 10 folders on the drive.  I can see them all except the files in the Videos folder.

Just if your a bit rusty good info here: [https://www.tecmint.com/recover-deleted-files-using-testdisk-in-linux/](https://www.tecmint.com/recover-deleted-files-using-testdisk-in-linux/)

---

### Post by ajgreeny on 2022-03-03
I am definitely running out of obvious ideas here but how did you get those video files on to the external drive; did you move them using a GUI, eg file-manager in either Windows or Ubuntu?

I know very little about Windows any more but I wonder if you created a link or links to that Videos folder in the source rather than actually copying or moving the actual files, and you are no longer seeing the files as the destination is no longer mounted or available.

---

### Post by shane_faulkinbury2 on 2022-03-06
I rewrote my OS to my 2 TB hard drive and this the first time I inserted my external nothing showed.  I'm going to assume that it's because I formatted it FAT32.  I guess I have to find another computer to see them or do another install and try again.  I'm watching a movie on the drive with it connected to my Roku right now.

---

### Post by shane_faulkinbury2 on 2022-03-06
Total size of video files is about 1.4 GB.

---

### Post by #&amp;thj^% on 2022-03-07
The 1.4 Gig would have copied over to the Fat32 drive just fine, "Unless" say you copied 3 or 4 folders with 1.4 gigs inside each one=4.2gigs/5.6gigs.
That will more than likely fail or at best corrupt files.

---

### Post by TheFu on 2022-03-08
Interesting.  I have a few guesses for what could be causing the problem.

Let's gather some information to start.
Please run these command while booted in Ubuntu WITH the external device connected AND mounted:
```
df -hT -x squashfs -x tmpfs -x devtmpfs
lsblk -e 7 -o name,size,type,fstype,mountpoint
mount
```

Please post both the exact command and exact output back here, each command+output wrapped in 'code tags' so the columns line up.
[Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code) explains code tags.

I suspect a Try Ubuntu environment is actually being used, so the copied files in ubuntu are just there for that boot.  The commands will show some proof of the situation for the storage and the last command will show us the options used for each mount.

---

### Post by shane_faulkinbury2 on 2022-03-09
> **TheFu said:**
> Interesting.  I have a few guesses for what could be causing the problem.

Let's gather some information to start.
Please run these command while booted in Ubuntu WITH the external device connected AND mounted:
```
df -hT -x squashfs -x tmpfs -x devtmpfs
lsblk -e 7 -o name,size,type,fstype,mountpoint
mount
```

Please post both the exact command and exact output back here, each command+output wrapped in 'code tags' so the columns line up.
[Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code) explains code tags.

I suspect a Try Ubuntu environment is actually being used, so the copied files in ubuntu are just there for that boot.  The commands will show some proof of the situation for the storage and the last command will show us the options used for each mount.

Sorry guys, I decided to reinstall Ubuntu 20.04.3 and start over.  dBanning now and writing from my ISO tonight.  Will get back to this after I copy my video files from external drive to computer HDD.

---

### Post by shane_faulkinbury2 on 2022-03-13
This one has dumbfounded me all.  I formatted it in NTFS and FAT32, rewritten Ubuntu 20.04.4 and 20.04.3 .   Nothing works.  I'm going to half to chalk it up to a bad external drive.  I guess I should just get a new one before this one totally bombs!

---

### Post by gdpetti2 on 2022-04-23
Should I start a new thred? I have a very similar problem with a USB external flash drive... 2TB.... new, says capable with Linux2.4 X etc and most newer Mac, Win etc... 
Transferred folders with files... as I've always done with my other flash drives. Seemed fine at first... but later learned most of the folders were empty. A few still had their files in them, but all the others were empty. I deleted those and tried again. It seems that the folders are/were empty but the files are still on the drive, as a click on  'properties' shows that the contents is still at the same Gb level. Also, when I tried again, I see those files listed where they were transferred to but cannot access them. I tried sending a video file later that seemed to work. I tested it and it did, but a few hours later, the folder was empty again... yet the 'properties' click didn't show any reduction in the usage on the drive. So all those files might be recoverable? Or is this simply a bad flash drive? No  problem with my other flash drives using any of the USB ports on the side of this computer running that last Ubuntu from 2020.... it seems only this flash drive is the problem... the files seem to be there, but 'disappearing' from view. A few folders still show them, but most do not.... weird. What happened to them?

Not the tech type. My computer is a Galago Pro frm 8 years ago... need a new mobile one, but this one has worked well.... computer seems fine, just this USB flash drive... again, none of the other ones have any problems. Since I deleted most of those folders, does that make any file recovery a bigger problem? Again, in 'properties', it seems nothing has changed in terms of disk usage, space available.

---

### Post by shane_faulkinbury2 on 2022-06-22
Hey all.  Sorry I didn't close this thread but I still cannot see my external Seagate HDD.  I got busy with work and couldn't get back to this.

I can see the HDD in Disks on Ubuntu, but fidsk shows nothing.  Can I do anything to resolve this?  At this point I do not care what was on the disk.  I just want to delete everything and start over.  Do I need to create a partition and if so, how do I do that to a disk that cannot be seen. fdisk and parted cannot see it.

---

