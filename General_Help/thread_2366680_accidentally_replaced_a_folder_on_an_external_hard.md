---
title: "accidentally replaced a folder on an external hard drive"
date: 2017-07-20
forum: General Help
---

### Post by treffry on 2017-07-20
Hi guys,

This is my first post and I'm hoping for some help regarding a data recovery issue.

I want to know if it's possible to recover replaced/overwritten files.

Here's the story;

I was moving some files from my laptop into my external seagate hard drive and annoyingly I accidentally replaced a folder there that had the same name.
This was done on a mac, not windows (usually windows just merges the files if they have the same name).

After the folder was in the process of being replaced I realized instantly what was happening and I cancelled the action while it was still transferring the files, but it was too late and a new image for the folder was created, overwriting all the old files in the folder. I was not able to undo this action. This is a major flaw in the OS X operating system (according to the internet).

I've done quite a bit of research online about this matter, which is a surprisingly common disaster for some people. Replacing a file is much much worse than accidentally deleting a file. Deleted files can be recovered quite easily, but it seems overwritten files are a lot more complex. Files that are overwritten are analogous to writing something in pencil, rubbing it out and then writing something new on top of it. But there are conflicting reports on this and it seems there are many people online who have recovered overwritten files, however there's also many reputable sites that claim that overwritten file recovery is a lost cause.

There's a few things that might save me. Firstly, the original folder was huge- containing at least 20 gigs worth of video files. The new folder that overwrote it was tiny by comparison at around 500 megabytes. This means that potentially only 500 megabytes of the 20 gigs was overwritten, if that, because i cancelled the transfer after 10 seconds. Hopefully a large bulk of the original 20 gig worth of files is still hiding somewhere on the external hard drive.

Here are the specs:


[LIST]
[*]I was using a macbook air, dragging files onto a seagate external hard drive. The replaced folder was on the seagate, replaced by a folder dragged over from my mac. The files within the folder were video files.

[*]The file destination was the external hard drive so I'm assuming if there's anything to recover it will be on the external hard drive, not the macbook.
[*]MacBooks use a destination file system that is HFS, however the seagate apparently converts it NTFS. I'm unsure if the file destination is HFS or NTFS in my case, and if this makes much difference to ease of file recovery.
[*]I have not touched the hard drive since I replaced the folder by mistake. I have advoided writing anything new to the hard drive incase it overwrites hidden data I might be able to salvage.
[*]I think my seagate is a SSD, which apparently is beneficial in the likelihood of recovering overwritten files.
[/LIST]

In conclusion, I think my biggest likely saving grace here is that I didn't overwrite the 20 gigs with an equivalent huge file. Intuitively this feels like the original files must still be buried somewhere on the hard drive, but I am far from a computer tech. I'm hoping the extremely tech savvy people on Ubuntu can assist me with a prognosis and possible course of action.

And yes, I know I should be backing up my files. Ironically the seagate was acting as my backup hard drive and I was dragging files there in order to back to them up. Ouch.

---

### Post by deadflowr on 2017-07-20
Unfortunately anytime you overwrite any file it becomes that much more difficult to recover.
Best most can suggest, beyond going to paid for professional forensic specialists, is to see what testdisk can do:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")
[https://help.ubuntu.com/community/DataRecovery]("https://help.ubuntu.com/community/DataRecovery")
[https://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/]("https://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/")

---

### Post by treffry on 2017-07-20
difficult but not impossible?

It seems there are many people on the internet, in my situation, who have managed to recover 'replaced' files.

Thanks for the links

---

### Post by dragonfly41 on 2017-07-21
I am adding to the advice given by deadflowr above.

The first point to make is that if the overwritten data is valuable then you should consider cloning your (overwritten) partition into another external drive.   You can then work on recovering the cloned drive keeping your original in reserve.

The second point is that in recovery after many, many hours of scanning the target data you will find that you need somewhere to actually save any recovered files. It can be annoying to scan for files and then find you don't have capacity to save them. You cannot save them in the target drive being recovered since you might overwrite data.   So you will need yet another device (> 20 GB in capacity) to save recovered files.

The third point is that you might look at photorec as well as testdisk.   Testdisk may recover named files but you will lose file names with photorec.  You write that most of the content are video files so in photorec set the filters to look only for video files.

There is a useful explanation of photorec usage here (although it refers to windows).  Read also the cgsecurity.org site.

[http://www.wikihow.com/Recover-Overwritten-Files](http://www.wikihow.com/Recover-Overwritten-Files)

You correctly point out that only part of the 20GB folder will have been overwritten.

---

### Post by treffry on 2017-07-21
Dragonfly, this is a very helpful response. I thank you most kindly. I am encouraged by this. I will post results.

---

### Post by dragonfly41 on 2017-07-22
Hopefully you are making some progress.

If you wish to study this subject of "forensic data recovery" in greater depth then I suggest that you search for discussions with "forensic" as the forum search pattern.

Here is one such [discussion ]("https://ubuntuforums.org/showthread.php?t=2336783&highlight=forensic")about slicing data.

And the Ubuntu chapter on [data recovery]("https://help.ubuntu.com/community/DataRecovery").

To avoid making the mistake you describe perhaps install LuckyBackup from software centre.  This uses the "dry run" option as in grsync so that you can see what is happening before any overwriting.

---

### Post by treffry on 2017-07-22
thanks dragonfly. How does one go about cloning an overwritten partition? I want to be careful and keep the original in reserve as you recommend. I am also a beginner when it comes to any of this sort of stuff (I find photorec's user interface a bit intimidating and confusing to be honest - definitely want to have a reserve drive in case I mess up my first attempt at data recovery).

Would I be better off just cloning the whole hard drive just to be on the safe side?

Thanks for the link - The thread with the guy trying to rescue a chunk of a partially overwritten mp3 was interesting. Luckily for me I have multiple files I am trying to rescue, not just a chunk of one file.

---

### Post by yancek on 2017-07-22
The link below is the "clonezilla" home page which you will see by going to that page that is what it is designed to do.  I would suggest that you read it carefully before downloading the iso and creating a bootable CD/flash drive with it.  There is a link on the left side of the page to a very extensive FAQ which should be helpful.

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by dragonfly41 on 2017-07-23
treffry, you wrote in your first post ..

> &#8220;I'm unsure if the file destination is HFS or NTFS in my case, and if this makes much difference to ease of file recovery.&#8221;

In fact if format is _not_ ext2/ext3/ext4 then the R-Linux idea below (to use a GUI)  will not help you. R-Linux does not recognise NTFS.   Ironically if overwritten files are in NTFS format you might get results by attaching your cloned USB drive to a Windows/Mac laptop for data recovery experiments.

...

Photorec _does_ recognise NTFS format.

See here ..

[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step#File_system_type](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step#File_system_type)


Photorec manual is here ...

[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

Note this advice in above page.

> Forensics users can use the parameter /log to create a log file named photorec.log; it records the location of the files recovered by PhotoRec.

...

Posting the earlier link to the discussion of data slicing reminded me of R-Linux referred to in that thread.

By some coincidence I am beginning to learn the features of R-Studio (for a separate development requirement, not forensic data recovery) so out of curiosity I decided to try out R-Linux to extend my understanding.

I downloaded RLinux5_x64.deb from this site ..

[http://www.r-tt.com/free_linux_recovery/Download.shtml](http://www.r-tt.com/free_linux_recovery/Download.shtml)

I have GDebi Package Installer and I launched that to open and find the downloaded *.deb file in Downloads folder.

Then I installed R-Linux.

When installed it appears under Applications > System Tools > R-Linux.

A GUI opens and if you have now cloned your overwritten drive (by clonezilla), attach the clone (not the original drive held in reserve) to start recovery (but note on ext2/ext3/ext4 formats only).

Manual is here ..

[http://www.r-tt.com/downloads/Free_Linux_Recovery_Manual.pdf](http://www.r-tt.com/downloads/Free_Linux_Recovery_Manual.pdf)

[http://www.r-tt.com/Articles/File_Recovery_Basics/](http://www.r-tt.com/Articles/File_Recovery_Basics/)

[http://forum.r-tt.com/data-recovery-f13.html](http://forum.r-tt.com/data-recovery-f13.html)

...

As a general word of advice never drag files or folders from laptop to your external device. Use a package such as LuckyBackup (there are others) to run pre tested sessions.

---

