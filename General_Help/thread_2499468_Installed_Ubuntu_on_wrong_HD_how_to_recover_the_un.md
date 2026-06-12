---
title: "Installed Ubuntu on wrong HD how to recover the underlying / deleted partition"
date: 2024-07-28
forum: General Help
---

### Post by greensoma on 2024-07-28
Hey guys,

I am in need of help. I reinstalled Ubuntu 24.04 some time ago, and selected the wrong harddrive in the install dialogue. So the installer formated the disk an installed a fresh Ubuntu over my important data.
I quite fast relized what has happened and did a raw compy of the drive with DD and stoped using this Disk. 
I tried to recover the data with photorec and testdisk but could only find the files of the newly created ubuntu installation. No data from the old partition so far.

Can you help me?
Is there even a chance to recover any data?

What can I do?

---

### Post by TheFu on 2024-07-28
> **greensoma said:**
>  
Can you help me?
Probably not.

> **greensoma said:**
>  
Is there even a chance to recover any data?Only if you have backups from before the install.  If you had those, then you wouldn't likely be posting here.

> **greensoma said:**
>  
What can I do?

Almost nothing.  Even using testdisk and photorec to restore files will be crazy painful.  There are likely hundreds of thousands of files that can be restored, but they will all be randomly named and there are likely to be 10+ versions of each, so you'll have to manually compare each of those 10 files to decide which is the latest.  Do you see the problem?  Even with just 50 files, restoring specific files using testdisk/photorec is painful and that assumes the entire disk was properly zeroed BEFORE any new files were added and before the overwrite happened.

If you are like everyone else, you'll have some hope until you try to do some manual restores. After 1-3 weeks of doing that, you'll finally see how huge the task is and probably give up.  The best outcome I can even hope for you is that you get backup religion and start creating at least weekly, if not daily, backups.  

Sorry to be so pessimistic.  Others will see what I've written and try to provide some hope.  You may be willing to pay a data recovery service.  For easy restores, those typically run $300.  For hard restores, add a 0 for $3000.

All because a $40 external USB HDD wasn't used to make backups. Live and learn.

---

### Post by currentshaft on 2024-07-28
> **greensoma said:**
> 
What can I do?

Recover from a recent backup.

---

### Post by dragonfly41 on 2024-07-29
Burn this sage quote into your memory ...
[https://www.goodreads.com/quotes/626466-for-the-want-of-a-nail-the-shoe-was-lost](https://www.goodreads.com/quotes/626466-for-the-want-of-a-nail-the-shoe-was-lost)

In the context of this thread the "nail" is ...

> 
[COLOR=#000000]All because a $40 external USB HDD wasn't used to make backups. Live and learn.[/COLOR]

---

### Post by greensoma on 2024-07-30
[COLOR=#000000]Hey congrats guys,[/COLOR]

[COLOR=#000000]I lost my important files and feel even more down now Well done! Really? What do you think will be the first thing you realize when you lost all the data. Yes ... you name it.[/COLOR]

[COLOR=#000000]@TheFu thanks for your provided informations. Thats quit exactly what I went through! I mentioned it in my question....[/COLOR]

[COLOR=#000000]I am using a backup system with cloud storage and external harddisk but unfortunatly the files lost weren't mirrored to those places. [/COLOR]
[COLOR=#000000]What I like to now is if there even is a chance to extract some files from the overwritten harddrive?[/COLOR]
[COLOR=#000000]How is the Ubuntu installer procedure and formation process? Will it overwrite all the files? Will only the partition be deleted and the files could still be there? [/COLOR]
[COLOR=#000000]Is there maybe another or better thing I should try beside from Photorec or Testdisc? Is there a way to somehow restore the old Partition?[/COLOR]

---

### Post by psychohermit on 2024-07-30
Hate to say it but I think you're out of luck, the files were overwritten most likely.

Sorry  about that,
--glenn

---

### Post by TheFu on 2024-07-30
> **greensoma said:**
> [COLOR=#000000] 
[COLOR=#000000]What I like to now is if there even is a chance to extract some files from the overwritten harddrive?[/COLOR]
[COLOR=#000000]How is the Ubuntu installer procedure and formation process? Will it overwrite all the files? Will only the partition be deleted and the files could still be there? [/COLOR]
[COLOR=#000000]Is there maybe another or better thing I should try beside from Photorec or Testdisc? Is there a way to somehow restore the old Partition?[/COLOR]

Have you read this? [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

I think you don't understand how complex getting **any** of the files back will be.  This only works if they weren't overwritten, which is a crap shoot. Nobody knows.  But if you have 100GB partition and the OS install took 20GB of that, then 80% of the available partition could be there.  

That really isn't very helpful, since none of the filenames will have been retained.  At restore time, you'll get hundreds of thousands of files that begin with "f" and followed by a random number, and a mostly correct extension, if the restore tool can figure out the type of file.  For media files, figuring out the type of file seems to be easier.

So, you have 
f2349823482.txt
f2349823483.txt
f2349824482.txt
f2349844483.txt
f2349844586.txt
f2349853483.txt
f2349863482.txt
f2349873483.txt
....
for 100,000 files.
Is that helpful?  Some of those files will be slightly different versions of the same file.  Only you manually comparing them will work.
There are no directories.  All these random filenames will be in the same directory.  Some will be OS files. Some will be data. Some will be partial files.  No way to tell except manually looking.

Do you see the issues now?

You could have been restoring files for a day now and started manually going through all of them rather than asking more questions. It won't make the task any less difficult.  Also, you need to restore the randomly named files onto different storage.  All permissions, ownership, group, ACLs, xattrs will be lost too, so the OS files will be useless.

You can pay someone else with commercial tools to restore the files.  Depending on the file system type, it may be easier.  Some MS-Windows only tools are pretty good, but they probably don't work on non-Windows file systems.  Sorry, I don't recall what you have.

I think you trying to recover the data is mostly futile.  There are very specific situations where I've been happy with the data recovery results and you don't have that situation.  Basically, it is only if the partition was completely zeroed before a file system was put onto the partition and only a few files (less than 100) were added to the file system before I needed to recover them.  After recovery, I still had to manually look through the files, rename them, decide which were the most recent and not temporary files, before choosing which to keep.  Doing just 100 files took a few hours.  Hopefully, you see the scope of the problem better now.

---

### Post by greensoma on 2024-07-30
> **TheFu said:**
> Have you read this? [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

I think you don't understand how complex getting **any** of the files back will be. 

That is why I am here. If I would understand all of this I might not ask for help. Instead I might guote some posh one liners which help not at all. Like in the answeres above. 

That is what I need to know and asked for. Since I dont understand what exactly is going on I decided to come here and ask people who might know. 
I know about the fact that many of the files might be lost. If you tell me the installation manager overwrites everything I stop trying. But there seems still a chance. Atleast that is how I understand your answer. Thanks for letting me know.

As said two times now before above. I used testdisk and photorec allready and know what it gives me. And yes. If there would be at least some of the files I am looking for that would be great. But that is my problem. It seems that ist is only files from the newly created partition. That brought me to the asumption that maybe the installer overwrites everything in a way that nothing can be rescued. But since your answer I now know that might be niot the case. So I will try further.

I see the issue all the time :) with photorec. No need to explain this to me. My question is somewhere else.

What I axtracted from the answeres here is the following:

- There might be some data which is [recoverable]("https://www.dict.cc/?s=recoverable"). Great!
- Installer doesnt overwrite the data with ZERO or else. So also gives me some hope that there might be some files to find.
- Photrec is quite a painfull procedure. I am ok with that and the files I am searching for are easy to identify by fileextension, size or preview. There might also not be much of them. So there is still a chance to find them.
- Windowstools or expert service are still an option. I will look into this.

What I like to know before I work my way through [ https://help.ubuntu.com/community/DataRecovery]("https://help.ubuntu.com/community/DataRecovery") 
Is there a tool on this list which might give me more success then photorec or testdisk?

---

### Post by dragonfly41 on 2024-07-30
IF you recover a batch of unidentified files as in photorec then as advised it will be difficult to unscramble broken eggs. However with your existing system you might experiment with Recoll to index your entire file system to see what Recoll can do.  For example if you can remember key words in your lost files you can search for such keywords. Hover cursor over Recoll query field to see a cheatsheet with examples. Even if this does not recover anything Recoll will be a valuable tool to learn for navigating the desktop universe. Also search "Ubuntu Forensics".
Where you have a large batch of unknown files I would employ front end automation scripts to inspect each file in a batch run. Remember Recoll is not a recovery tool it is an indexing tool. RLinux is another recovery tool to experiment with.

To gain another opinion subscribe to Phind.com (AI assistant) and craft a prompt such as here:

> If a working Ubuntu desktop with important data (without backup) is over installed by a fresh Ubuntu is it feasible to recover data from the overwritten partition. What forensic data recovery tools are recommended to recover past data?

Forensic tools such as Foremost and Scalpel will be listed.

But one important piece of advice (other than backing up in the future) is to stop using the mangled drive and analyse using a different drive with forensic tools installed. Where for example did you save testdisk recovered files? Not into the drive you are hoping to recover.

It might be prudent to clone your existing mangled drive so that you experiment on the cloned version.

I have the benefit of a StarTech dual docking bay (each bay containing a drive) where I can plug in two caddies as well as using LiveUSB to run tools such as Foremost, Scalpel etc.

But I do not want to give false hope. It is a challenge.

---

### Post by yancek on 2024-07-30
> But if you have 100GB partition and the OS install took 20GB of that, then 80% of the available partition could be there.   

In that case if the partition was nearly full of various data, then theoretically up to 80% could be recovered.  As pointed out above, the chances of recovering data are better if you immediately realized what happened and immediately stopped using the drive and made a copy of it on another drive and have been trying to recover from that drive.  If you used the drive for even minimal time, your chances of recovery are very limited.  The  problem is that a system generally is installed on the beginning of a partition and that is generally where your data is.   

>  Is there a tool on this list which might give me more success then photorec or testdisk?         

I'm not familiar with all the tools in the link but it has always been my understanding that when all else fails, use testdis and photorec.  If the data is important to you and you have the time, no reason to not keep trying.  You might save at least some data.  Good luck.

Have you tried recovering the partition table as discussed at the testdisk site.

[https://www.cgsecurity.org/testdisk_doc/partition_recovery.html](https://www.cgsecurity.org/testdisk_doc/partition_recovery.html)

---

### Post by oldfred on 2024-07-31
You mention hard drive. Was it HDD or SSD.
If SSD, trim is run on a regular schedule and that clears unused block. Not sure if new install also runs trim or not.

I have used Photorec & it recovered lots of files. I only needed 30 or 40 .txt files & it recovered many more. As mentioned above many duplicates & partials.
I did have an older backup, but the compare & grep process, I could not even be sure which was newest update to file in many cases. 
If photos, file has internal data you can use to rename.
 I now add a # filename as first line in every text file and backup more frequently. 

If photorec is not finding anything, it does not look good as it just scans entire drive looking for anything that looks like a file.

---

