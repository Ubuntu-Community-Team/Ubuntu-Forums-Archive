---
title: "Recover a LOT of accidentally deleted files from an external hard drive?"
date: 2019-01-01
forum: General Help
---

### Post by RallyDarkstrike on 2019-01-01
Hey all,

I've got an odd situation - hopefully you guys will be able to help! A bit of background first - I do computer work on the side, mostly Windows and some Mac stuff as VERY few people around here use Linux. I'm predominantly a Windows guy (I have a Win10 Core i7 desktop), but am also a huge Linux fan as my HP laptop runs Linux Mint 19 MATE.

Now, I've had to recover files on Windows many times before for both myself (once and awhile) and clients (often) and I usually use the software Recuva. It works great and usually gets almost everything back the client needs recovered. However, I have a lady who just called that accidentally deleted a few folders containing 70 or so gigabytes off of her backup drive. She has a laptop running Ubuntu 12.04 (ancient!) that I was going to wipe and upgrade to the most recent version of Ubuntu for her tomorrow morning - she accidentally deleted her backup while backing everything up for that upgrade...

I know file recovery tools for Linux exist, but where I have not used them before, does anybody have any suggestions for one that I could use to try and get her files back? I'm pretty much in the dark on this as I have no idea what filesystem her external drive nor her laptop's drive was formatted to (I don't have either in my possession yet until tomorrow morning), but I am assuming probably the external drive has the standard formatting it came with from the factory, i.e. probably NTFS or FAT.

The way she described the situation to me was that she dragged the folders from the backup drive to the Trash on her desktop thinking they were only older copies of the things she was about to be backing up to the drive from the laptop, then copied said backup from her laptop back to the external drive, then emptied the Trash. After she emptied the Trash, only then did she remember the folders she deleted did contain older copies of what she was now backing up, but also a huge mass of even older files from prior that she had no other copies of.

TL;DR. Any suggestions for a program I could use to recover deleted files off an external hard drive from the Trash of an Ubuntu installation...?

Cheers and thanks for any help and suggestions!

---

### Post by clementc on 2019-01-01
Hi [**RallyDarkstrike**]("https://ubuntuforums.org/member.php?u=1212449"),

If the external hard drive of your client is using the following filesystem then installing and using [TestDisk]("https://www.cgsecurity.org/wiki/TestDisk") would be my first go: FAT, exFAT, NTFS and ext2

Please refer to [this page]("https://askubuntu.com/questions/443376/recovering-very-important-lost-data-from-external-hard-drive-when-copying-it") for instructions on how to proceed.

Edit: please make sure to tell your client to stop using her external hard drive asap as anything she does could overwrite the space left by the deleted files and make them unrecoverable.

Edit 2: if indeed the external hard drive's filesystem is NTFS or FAT, Recuva might still help recover the files as well.

---

### Post by apmcd47 on 2019-01-01
Look at these articles and download one of the suggested live CDs. It looks like PhotoRec is the utility you need on either SystemRescueCD or Knoppix.

Andrew

[https://www.linux.com/learn/get-your-data-back-linux-based-data-recovery-tools]("https://www.linux.com/learn/get-your-data-back-linux-based-data-recovery-tools")

[http://www.linuxandubuntu.com/home/5-best-data-recovery-tools-for-linux-to-recover-data-or-deleted-partitions]("http://www.linuxandubuntu.com/home/5-best-data-recovery-tools-for-linux-to-recover-data-or-deleted-partitions")

---

### Post by yetimon_64 on 2019-01-01
> **RallyDarkstrike said:**
> ...
The way she described the situation to me was that she dragged the folders from the backup drive to the Trash on her desktop thinking they were only older copies of the things she was about to be backing up to the drive from the laptop, then copied said backup from her laptop back to the external drive, then emptied the Trash. After she emptied the Trash, only then did she remember the folders she deleted did contain older copies of what she was now backing up, but also a huge mass of even older files from prior that she had no other copies of....
When dragging the files "to the Trash on her desktop" the actual file data would have still remained on the external drive; Windows "deletes" files only by moving the file allocation table references to the data NOT by moving the actual file data as far as I understand Windows (my use of windows was from 3.11 to win7, or about 20 years of usage). If the external drive has been subsequently written to the older data may be overwritten by the sounds of this.

I would definitely try [COLOR=#000000]clementc's suggestion of using testdisk (or recuva from windows) on the external drive but I suspect the new data written to it may have caused some data loss as the most likely outcome. Running testdisk on the Windows install would be highly unlikely to recover anything as file data remains in place when windows "moves a file" to the rubbish bin, only the file allocation table references are changed by such as far as I'm aware. Overwritten data (if such has occurred) may not be recoverable with any of the above mentioned tools.

Good luck with this, hope you do have some success with testdisk (or recuva from windows) on the external drive. Cheers, yeti. [/COLOR]

---

### Post by RallyDarkstrike on 2019-01-01
Thanks folks - I'll see what I can do. I warned her not to use the drive at all until I could look at it.

@Yeti - Yes, I'm aware that's how it works with Windows, but as she deleted them in Linux by first dragging them to the Trash from the external disk, does that mean the files were moved to the laptop before they were deleted, or (like Windows), would their remnants still be on the external drive?

---

### Post by clementc on 2019-01-01
Hi [**RallyDarkstrike**]("https://ubuntuforums.org/member.php?u=1212449"),

Although we will wait for yeti's confirmation, my understanding is that files moved from a removable medium to the Trash do not get transferred to the user's PC but to a trash folder on the external drive itself before they get "permanently" deleted once the Trash is emptied.

---

### Post by yetimon_64 on 2019-01-01
> **RallyDarkstrike said:**
> Thanks folks - I'll see what I can do. I warned her not to use the drive at all until I could look at it.

@Yeti - Yes, I'm aware that's how it works with Windows, but as she deleted them in Linux by first dragging them to the Trash from the external disk, does that mean the files were moved to the laptop before they were deleted, or (like Windows), would their remnants still be on the external drive?
Not entirely sure if this was done from linux, if the actual data was moved. Although for compatibility with windows I suspect it would be much the same method used. Wait for further advice regarding that.

If there is a difference, or someone else suggests linux does it differently; I'd try with testdisk 1st on the external drive (before any further writing is done to that drive) from a linux install.

On rereading the opening post; if the files were deleted, that is the "trash was emptied", **after** the new backups were copied over there may be a better chance of recovery with testdisk. All the files may still be present on the external drive, if this is the case. I originally read the opening post as the other way around. It is extremely important, as has already been noted by clementc, that the extenal drive is not wriiten to again until after any recovery of files is done.

---

### Post by RallyDarkstrike on 2019-01-01
Thanks Yeti - I realized that order was important with how things were deleted off the disk as that same situation matters under Windows as well. I had specifically asked her on the phone what order everything happened in and what I relayed above is what she thought had taken place, to the best of her knowledge. I won't know for sure until tomorrow, but here's hoping she got the order right as that means there is a chance I can get her stuff back...

I'll keep you folks updated - kudos for the replies! :)

---

### Post by HermanAB on 2019-01-02
When you get the disk, immediately make a clone of it onto another disk (dd or cat), then work on the clone.  Do not work on the original.

---

