---
title: "On flash drive, cant move to trash or delete things or rename"
date: 2018-03-19
forum: General Help
---

### Post by pretty_whistle on 2018-03-19
[IMG]http://i67.tinypic.com/juv43p.png[/IMG]

See the right click menu on this Lexar flash drive? Some options aren't available like being able to rename, delete, & move to trash.  The drive keeps doing this. After I first plug it in it's fine then it does it every time. I've tried rebooting and it still does it. I've tried unplugging & replugging it but still the same issue.  I've also tried plugging it into different ports, same thing happens.

After it works at first I try to run my backup program on it, luckyBackup, the drive does it and the backup program tries to delete files and can't do it.  The drive runs ok till I run the backup program which makes it look like it's the backup program's fault but why would it be, it ran fine for months.

I have Ubuntu 16.04.4 LTS with Unity desktop. My computer is only a year old and the flash drive is new so I doubt it's that.

Any help is appreciated, thanks!

---

### Post by pretty_whistle on 2018-03-19
Any help?

---

### Post by pretty_whistle on 2018-03-19
Well I stopped using the backup program and tried copying one folder into it's copy on the drive, it did it again anyway except this time every file and folder got a lock on them and a permissions error came up saying it was read only.  I'm using the admin account so how can it be read only?  Help!

---

### Post by pretty_whistle on 2018-03-19
All my flash drives are messing up. Copying folders/files produce errors.

---

### Post by yancek on 2018-03-19
How big is this flash drive?
Is this a full install of Ubuntu or something you created using software such as Rufus, unetbootin, UUI?

That's expected behavior for a Live system.  If as it seems, you have a full install are you trying to backup files on tthe flash drivel to another drive?

I've not used the software you refer to but generally, doing backup requires root privileges especially if you are backing up system files.  If you do a backup as root user (using sudo) then the directories and files will be owned by root which is one reason you would have the lock on them or would see the permissions error.  Simple enough to check the permissions.  If you are trying to access using sudo, you should not be seeing those errors unless a filesystem is corrupt.

> I'm using the admin account so how can it be read only?  

There are actually a lot of files which are read-only even for root though I doubt that is the problem.  What exactly do you mean by admin account?  Is this the primary user you created on install which has root/admin privileges by default? 

And how are you now trying to copy to your flash drives, GUI or terminal?

---

### Post by pretty_whistle on 2018-03-19
> **yancek said:**
> How big is this flash drive?
Is this a full install of Ubuntu or something you created using software such as Rufus, unetbootin, UUI?

That's expected behavior for a Live system.  If as it seems, you have a full install are you trying to backup files on tthe flash drivel to another drive?

I've not used the software you refer to but generally, doing backup requires root privileges especially if you are backing up system files.  If you do a backup as root user (using sudo) then the directories and files will be owned by root which is one reason you would have the lock on them or would see the permissions error.  Simple enough to check the permissions.  If you are trying to access using sudo, you should not be seeing those errors unless a filesystem is corrupt.

  

There are actually a lot of files which are read-only even for root though I doubt that is the problem.  What exactly do you mean by admin account?  Is this the primary user you created on install which has root/admin privileges by default? 

And how are you now trying to copy to your flash drives, GUI or terminal?

The drive is 32 GB.

Not installing Ubuntu or anything. Just trying to backup personal files and folders & I was able to do it with this backup program for a few years but then recently can't. Also when I don't use the backup program it does it anyway.

I checked permissions on it in case it got changed somehow but everything looks normal.

What I mean by admin account is that it's the account created when I installed Ubuntu.  Whenever I need to use sudo in the terminal I have to enter my password so I must not be accessing things by sudo normally.

How I'm trying to copy onto the flash drive is both using the backup program and doing it directly via opening nautilus (not using the terminal).  Doing both create the effect in question.

When I first insert the drive everything's fine, then I run the backup program and in mid copy the drive goes crazy again.  By the end of the copying I can't delete, rename, etc.  Weird.

---

### Post by pretty_whistle on 2018-03-19
I'm formatting the drive to see if it cures this. Maybe the file system is corrupt.

---

### Post by oldos2er on 2018-03-19
Which file system is it using?

---

### Post by pretty_whistle on 2018-03-19
> **oldos2er said:**
> which file system is it using?

fat32.

---

### Post by oldos2er on 2018-03-19
I would try the suggestions for using mount to mount the device with read + write permissions: [https://help.ubuntu.com/community/Mount/USB#Using_mount](https://help.ubuntu.com/community/Mount/USB#Using_mount)

---

### Post by pretty_whistle on 2018-03-19
Thanks for the help everyone.  I formatted the drive in case the file system was corrupted - it worked. Problem solved!

I'll mark this as solved.

---

### Post by pretty_whistle on 2018-03-19
> **yancek said:**
> If you are trying to access using sudo, you should not be seeing those errors unless a filesystem is corrupt.



I forgot that I did try that and still got the errors. So the file system was corrupt. No wonder formatting it solved it. You were right on this. Just letting you know......


P.S.

I had posted I had issues with all my drives, I was wrong and panicked. It was just the one, oops.

---

