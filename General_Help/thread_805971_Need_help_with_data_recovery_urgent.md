---
title: "Need help with data recovery *urgent*"
date: 2008-05-24
forum: General Help
---

### Post by MikeMLP on 2008-05-24
I freely admit that this is (mostly) user error, though I think Nautilus may be partially to blame.

Here is what happened:

My hard drive was getting full, and I wanted to clear off some space.  All of my work is located in /fat/School - a folder in a separate fat partition which contains all of my most important documents.

When browsing through nautilus, I saw /fat/school and /fat/School.  I'm pretty sure this happened because I accidentally clicked off of the folder I wanted to be and typed /fat/school (rather than /fat/School) in the nautilus location bar. 

So when both appeared to have identical contents, I chose to delete one of them.  Big mistake.  Since, I am guessing that both "folders" were in fact the same one, all of my documents were deleted.  Since it was a fat partition, there was no .trash folder for everything to be conveniently pushed into.

My guess is no, but are there any recovery tools out there that could help me?  I have not written anything to the /fat partition since this occurred.  And this should definitely result in a _huge_ bug report filed against nautilus.  Definitely.

Please, please please help!

---

### Post by mikewhatever on 2008-05-24
Use photorec [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec).
Instead of blaming a program, check before you delete.

---

### Post by Bakon Jarser on 2008-05-24
Don't panic.  It probably did not delete your data.  It probably just removed all links to the data.  It doesn't really delete the data until it needs to write to the area where the data is stored, so since you didn't write anything to the drive it should still be there.  It'll take some googling and some research but I'm sure you can find a good recovery program.  Depending on how important the data is, it may be worth it to pay for one.  Just make sure you find one that has some good reviews out there.

---

### Post by Bakon Jarser on 2008-05-24
By the way, use filelight or disk usage analyzer to find where your disk space is being wasted, not Nautilus

---

### Post by MikeMLP on 2008-05-24
mikewhatever:

> Instead of blaming a program, check before you delete.

I do blame the program, and I think I have good reason to.  If a mistake as simple as substituting a lower-case letter for an upper-case letter in the location bar of Nautilus results in the appearance of there being two folders, one in lower-case, and one in upper-case, when there actually is only one folder, and deleting one of the two folders which appear within said program results in data loss... I think that that is a serious usability problem.  As soon as I made this mistake, I realized what I had done.  But I do think Nautilus's behavior in this particular instance is deceiving.  If I had taken a few seconds more, I would have probably closed Nautilus, and opened it up again to make sure what I was seeing wasn't an illusion.  That I take blame for.  But that doesn't change the fact that Nautilus should not have exhibited such behavior in the first place.

I simply suggest a bug report, which is the correct way of handling these things.  Am I upset that I got burned?  Absolutely!   Do I chuck blame around senselessly?  No.  At this point, I'm almost positive Nautilus has an issue.  This isn't as simple as me not checking before I delete.

As soon as I have my data back, or determine that I cannot get it back, I will  attempt to reproduce, and file a detailed, well-explained bug report.  Until then, I have a different priority.

I thank you wholeheartedly for the link.  It looks promising, and I'm checking it out right now.

Bakon Jarser:

> By the way, use filelight or disk usage analyzer to find where your disk space is being wasted, not Nautilus

I have used disk usage analyzer in the past.  It is a wonderful program.  The reason why this happened is because the way Nautilus presented my data, it looked as though I had somehow ended up with a duplicate (and thus, needless) copy of my data on the drive.  I was actually trying to organize my files at this particular moment, (thus, Nautilus was the correct application to use) though clearing off some space was the overall goal.  I happened to notice this "duplication" of a ton of my data, and wanted to get rid of one of the duplicates - to save space and to help organization.  The problem was, my data wasn't duplicated. Nautilus made it _seem_ as though it had been duplicated.

---

### Post by Bakon Jarser on 2008-05-24
it was not a nautilus bug.  All of your drives are located in two places in the linux filesystem.  They are in /dev and in /media. dev shows all devices on your computer, media shows all mounted drives on your computer.  If you insist that it is a bug then it is a linux bug, not a nautilus bug.

---

### Post by tamoneya on 2008-05-24
is it possible that you just deleted the mount points.  Can you post the result of this command so that we can take a look: ```
sudo fdisk -l
```

---

### Post by MikeMLP on 2008-05-24
Bakon Jarser:

> it was not a nautilus bug. All of your drives are located in two places in the linux filesystem. They are in /dev and in /media. dev shows all devices on your computer, media shows all mounted drives on your computer. If you insist that it is a bug then it is a linux bug, not a nautilus bug.

No, no, actually, I still think it was a Nautilus bug.  I understand that my drives are located in two places on the linux filesystem.  That has nothing to do with the odd behavior I saw in Nautilus.  Nor has this anything to do with mountpoints or entire partitions being lost.  fdisk -l reveals all is normal (of course).

I have to run soon, but when I get back, I'll see if I can do a nice screencast of exactly what happened.  The short story is this:

My data was located at /fat/School, on a separate fat32 partition.  In the Nautilus location bar, I typed, /fat/school (notice the difference in case - my mistake).  Nautilus had the tree view up in the left pane, and I noticed that there was a "school" folder and a "School" folder.  I could do various operations on both of them, like right-click and select properties, expand the folder to see subfolders, etc.  As far as I could tell "School" and "school" were identical in contents, just not in name.  Because Nautilus showed two separate folders, I assumed that I had inadvertently created a copy of /fat/School, so I deleted /fat/school.  Immediately, /fat/school *and* /fat/School disappeared.  My data was gone.

mikewhatever:  PhotoRec worked, and worked well, however it did not recover my folder structure, file names, or other metadata, such as creation dates, modified dates, and others.  I don't really expect metatdata to be preserved, but I was hoping that I could have saved the folder structure and file names.  I cannot complain too much, however - I have my files back, so thank you, thank you very much!  Now I have a huge organizational task ahead of me, unless anyone can think of a way to pull out (at least) file names and folder structure.  I just figured I would throw out this question, since it would save me a lot of time.  I am quite happy just to have my files, however.

---

### Post by aysiu on 2008-05-24
This is the first I've heard of any file browser displaying the same directory twice with one display having a capital letter and one having a lowercase letter. Go ahead and file a bug report on it, but unless the developers can reproduce the error, there's not much they can do about it.

I'd say in the future if you have a confusing situation, cut and paste files to the trash instead of flat-out deleting them.

---

### Post by mikewhatever on 2008-05-24
I am really glad you got the files back and sorry it didn't work 100%. Moving beyond that, I'd advise keeping a backup of that partition. There are various solution for Ubuntu, if you don't like the one below, no big deal.
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by koenn on 2008-05-24
photorec, like other file recovery tools, scans your hard disk directly and has no knowledge of any filesystem related attributes such as filenames, timestamps, or directories, it just reads bits of the disk and reconstructs files from them.

I typed the path and name of an existing directory, but with different capitalization,  in Nautilus location bar. It said 'file not found', as expected. 
If that's really how you managed to lose those files, then it probably has to do with FAT32 filesystem, which doesn't distinguish between s and S, and thus could trick Nautilus in believing that there was both a school and a School directory, while on the actual file system, it's the same directory, so it would be deleted by deleting one of school or School. 

You could maybe file a bug against fat32 in Microsoft's bug tracker for not being compatible with Linux or Nautilus, but I doubt they'll fix it : even Microsoft doesn't recommend FAT filesystems anymore.

---

### Post by MikeMLP on 2008-05-25
I have uploaded a video of the behavior on YouTube, just in case anyone doubted my sanity ;).  The link: [http://www.youtube.com/watch?v=x1fsngMKQyU]("http://www.youtube.com/watch?v=x1fsngMKQyU")

koenn:

> photorec, like other file recovery tools, scans your hard disk directly and has no knowledge of any filesystem related attributes such as filenames, timestamps, or directories, it just reads bits of the disk and reconstructs files from them.

Thanks! I figured it was something like this.  Fortunately, I have finished the work I needed to do for the semester, and am not in a desperate situation.  Reorganizing will be a major pain, but at least I have the data.  Now, my focus is trying to make sure this does not happen again to anyone else.

I have two thoughts currently.  One is that somehow Nautilus has become corrupted on my system. I am hoping that someone with a dual-boot system and a fat-32 partition will be able to run a test on their box similar to the one in the video I have uploaded to confirm or deny this behavior.  The other thought, of course, is that Nautilus has a "usability bug."

> I typed the path and name of an existing directory, but with different capitalization, in Nautilus location bar. It said 'file not found', as expected.

I also did this, with my ext3 partition.  Everything worked as expected: "file not found."  This is exactly what is to be expected with a Linux system, a pickyness that I really do appreciate because it leaves less room for silly errors, like the one I have experienced.  I think this is the "right way."

> If that's really how you managed to lose those files, then it probably has to do with FAT32 filesystem, which doesn't distinguish between s and S, and thus could trick Nautilus in believing that there was both a school and a School directory, while on the actual file system, it's the same directory, so it would be deleted by deleting one of school or School.

My thoughts, exactly, and it appears to be confirmed by the video.

> You could maybe file a bug against fat32 in Microsoft's bug tracker for not being compatible with Linux or Nautilus, but I doubt they'll fix it : even Microsoft doesn't recommend FAT filesystems anymore.

This is where I respectfully disagree with you, my friend.  I am well aware of the suckyness of fat32, and totally agree with you there.  If I were to do my partitioning over again, I would not even think about adding a fat32 partition.  For one, it screws up permissions, making it useless as a /home backup area.  For that I have to use my Windows NTFS partition.  

Which brings me to another point:  When I created the fat partition for my data, it was just after Dapper had been released and before NTFS-3g was ready for widespread use.  An NTFS partition, a fat32 partition and an ext3 partition were common on dual-boot systems, and pretty much the preferred way to go for sharing data between the two installs.  In fact, I used aysiu's psychocats web site as a guide to help me partition.  It was invaluable, and aysiu really helped me understand how to make the transition to Linux.  aysiu is awesome!

Even today, flash disks for mobile data storage, and memory cards for cameras commonly come formated as fat-16 or fat-32 because it is the "lowest common denominator."

Maybe you are right and Microsoft does not recommend that fat be used anymore.  I'm pretty confident that they're referring to the Windows OS filesystem, though I'm not sure since you do not cite a source.  But regardless of that, fat filesystems remain quite common, and probably will continue to be common for many years.

I performed an identical test to the one in my video with a fat-formated flash disk mounted under Windows XP.  when I entered ~"/oh-no" in the path instead of ~"/Oh-no," the ~"/Oh-no" folder was entered into automatically.  The path changed from lower-case to upper-case on its own.

I expect this user-friendly behavior from Windows.  It can be debated whether Nautilus should correct the user's mistake or should say, "file not found"  The later would be the more linuxy way of doing things, and something which I certainly would not be opposed to.

If it is not my system which is corrupt, but if this is common, reproducible behavior on fat volumes (the same behavior as in the video resulted when I performed the test on a fat formatted thumb drive), then Nautilus should overcome fat's limitations by handling the situation in one of the two ways described in the paragraph directly above.  Clearly it is possible, since Windows handles it.  What it should not do is create folders that do not exist in tree view, confusing the user, and inviting them to make disastrous mistakes, like I just did.

I would like someone to confirm this behavior before I send off a bug report, so that I can rule out that my system is corrupt in some way.  I'm on Hardy, and I did a Gutsy->Hardy upgrade.

-Mike

---

### Post by koenn on 2008-05-25
> **MikeMLP said:**
> 
Maybe you are right and Microsoft does not recommend that fat be used anymore.  I'm pretty confident that they're referring to the Windows OS filesystem, though I'm not sure since you do not cite a source.

"the FAT32 file system is only supported in the Windows 98/95 and Windows 2000." - [http://support.microsoft.com/kb/100108/](http://support.microsoft.com/kb/100108/)
support for Win 2000 ended in June 2005 : [http://support.microsoft.com/lifecycle/?p1=3071](http://support.microsoft.com/lifecycle/?p1=3071)
It's not clear from the KB article whether they refer to the use of FAT32 for Windows system partitions only, hard disks only, or all uses including   removable media such as memory cards and thumb drives. They do mention that FAT is best on volumes smaller than 200 MB. They also have several sys admin guides that point out the disadvantages of FAT and advice to use NTFS instead. 

> **MikeMLP said:**
> 
If it is not my system which is corrupt, but if this is common, reproducible behavior on fat volumes (the same behavior as in the video resulted when I performed the test on a fat formatted thumb drive), then Nautilus should overcome fat's limitations by handling the situation in one of the two ways described in the paragraph directly above.  Clearly it is possible, since Windows handles it.  What it should not do is create folders that do not exist in tree view, confusing the user, and inviting them to make disastrous mistakes, like I just did.


I reproduced your problem in a Virtual Machine. Your sanity can go unquestioned. 
What happens, I suppose, is that
- user tells Nautilus to show /fat/School
- nautilus tells the filesystem something like 'get /fat/School'
- FAT filesystem returns a pointer to the directory to nautilus
- nautilus shows the directory the user requested

- user tells Nautilus to show /fat/school
- nautilus tells the filesystem something like 'get /fat/school'
- FAT filesystem ignores the case and returns a pointer to /fat/School
- nautilus finds that /fat/school exists (it got a valid return from the filesystem) and shows the folder the user requested : /fat/school.

Windows then probably also queries the filesystem to get the correct spelling/casing of the filename, but Linux tools don't do that because they expect a case sensitive filesystem and would have expected to get 'file doesn't exist' in stead of a pointer to the directory.
You can see the same behaviour in other tools such as cp, rm and ls
so it's not really a Nautilus issue.

---

### Post by MikeMLP on 2008-05-25
Very clear and informative response, koenn.  Thank you.

Perhaps this is something that should be looked into no matter where it is on the stack.  It might be non-trivial to implement a routine that can query the filesystem for case when fat filesystems are being used, but it may be worthwhile, since I don't think fat filesystems are disappearing any time soon, despite their drawbacks.  I think we can agree that the way this scenario is handled right now is suboptimal.  If I were to file a bug report, what package should I target in launchpad?  Should I go upstream instead?

Thanks,
-Mike

---

### Post by koenn on 2008-05-25
I'll admit that if I'd be using FAT filesystems routinely AND wouldn't use some sort of naming convention (all lowercase, sometimes camelCase for very long filenames) in filenames, AND didn't rely on tab autocompletion to find the correct paths and filenames, I would sooner or later make the same sort of mistake. So I agree the situation is less than optimal, but not much more.

It's more of a compatibility issue than a real bug imo, but if you want to file a bug report, i think it should be against the package that provides the interface to the fat filesystem - the fat "filesystem driver". Don't know what that's called. And it remains to be seen in how far those developers will be willing to work on a workaround for a flaw in a file system that might be considered obsolete. 

I suppose you could file in target; they'll take it upstream if need be.

---

### Post by Terry of Astoria on 2008-05-27
It seems likely that "fixing" Nautilus to work around FAT's dumb disadvantages would be an unappealing and thankless task. If I had the ability to do that I would be using my powers elsewhere. That said, you are right. I'll bet you that quite a lot of valuable data has been lost thru that loophole, and a lot could be saved if it were mended. The thing is, it's going to be personal data. It's the Dual-booters' data. . . . I bet you no one will ever fix that "bug". Serious data is backed-up, and isn't on FAT filesystems. 
   Once several years ago, I lost all my photos and some other data by getting hacked while running Windows 2000 and playing Unreal Tournament on the internet. I think probably a script-kiddie deleted my data or formatted my hard drive. I don't know, but it was gone. 
   I got all my data back by using Testdisk - it came from the same company I think that photorec comes from. It recovered the entire filesystem for me, not just raw files.
   I think I posted on that back then. It must be here somewhere. Here's the thread chronicling my adventure:
[http://ubuntuforums.org/showthread.php?t=293710](http://ubuntuforums.org/showthread.php?t=293710)

---

### Post by MikeMLP on 2008-05-29
While trying KDE 4.1 Beta 1, I did a similar experiment with Dolphin on the Binner OpenSuse Live CD.  Dolphin does not change the path to upper case when lower case is entered mistakenly, nor does it say "path not found" or something similar.

Neither, however, does it create a new duplicate folder in tree view.  That particular "feature" is what messed me up, and in Dolphin, I probably would never have noticed the difference in case.  I certainly would not have been seeing double.  And I would not have been tempted to press delete.  Dolphin does not handle the situation in an ideal way either, but it handles it much much better than Nautilus does.  I deem Dolphin "good enough."

I'm going to have to check if this functionality extends back to stable versions.  But Dolphin's behavior has convinced me that a bug should be filed against Nautilus.  I will do that shortly.  Whether anything gets done about it - that's anyone's guess.  In the mean time, I've been looking for an excuse to try KDE again, and this is as good of one as any in my book.  With 4.1 Beta 1 packages soon to be available for Hardy, I may just try that, after, of course, backing up all my data.

I've *only* got about 450 documents left to resort and rename...  I don't really mind doing it, since it was about time to clean and resort anyway.  But that will take me a few days at least.

As far as serious data being backed up goes - I agree.  But what about the person who types in the path incorrectly when they put their fat formatted CF or SD card into their card reader with some brand new pictures on it?  That data obviously hasn't had a chance to get backed up yet.  Nautilus invites that user to mistakenly erase their data.  No matter how much the user is inherently to blame, a bug is a bug is a bug.  It is a contributing factor to data loss.  And who are we to judge the inherent value of a person's data based on the filesystem they choose to use, or even worse, are forced to use, as in the case of memory cards for digital cameras?  I think that's a pretty common use case for the typical target Ubuntu user.

---

