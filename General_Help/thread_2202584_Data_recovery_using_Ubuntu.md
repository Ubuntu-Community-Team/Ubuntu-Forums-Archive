---
title: "Data recovery using Ubuntu"
date: 2014-01-29
forum: General Help
---

### Post by Tanchistu on 2014-01-29
My laptop is not booting due to HDD errors. I am running Ubuntu from a DVD and I am trying to copy my documents to an external HDD.

The problem is that I cannot find the documents that I had on the Desktop. I searched under C://Users/Username/ ...

Is the data protected? I never used a password on my laptop.

---

### Post by deadflowr on 2014-01-29
What was the OS that had the files?
Ubuntu or Windows?

Which version as well.

---

### Post by Tanchistu on 2014-01-29
windows 7, sorry for missing that.

---

### Post by deadflowr on 2014-01-29
Here's a somewhat old guide, but the core of it should still hold.
[http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)

The important things are the fdisk -l command to find the right partition, and the mount commands to properly mount the ntfs partition that the windows is on.

Your files are normally somewhere in the documents and settings section.(I would think).

---

### Post by Tanchistu on 2014-01-29
That is exactly what I did, just that when I look into "/Documents and settings/MyName/" the folder is empty.

I can access and copy any other folders, just not what was on my "Desktop", I cannot browse to my "Desktop" folder from Ubuntu.

---

### Post by tgalati4 on 2014-01-30
Did the drive fail suddenly or was there a virus?  Install *smartmontools* from the Live DVD session and check the SMART parameters of the drive.

You want to determine if the drive failed due to a hardware problem and took your personal files with it--a head crash that can cause massive data loss.  Or, was your computer acting strange because it had a virus and the virus took out your files.  It seems strange that only your personal files are missing.  Is the rest of the disk OK?

---

### Post by Tanchistu on 2014-01-30
The laptop is an HP and it says that the disk will fail, and if I go past that, the windows will never load, it either crashes with a blue screen, or it stays like that for hours or it says that it cannot load some file. And yes it says something about SMART.

The HDD is still functional, I already got about 150GB of data from it, is just that some of the most important files were on desktop, and the folder that was supposed to have the desktop folder "/Users/Username/" is empty. To me it seems there is some kind of protection of the files, and you can only see those files if you are logged into the machine with that username. I didn't had any password.

I am probably asking this question in the wrong forum ...

---

### Post by bashiergui on 2014-01-30
Have you looked at the size of /users/username? Why not copy the whole /users folder over and see what comes over.

---

### Post by Tanchistu on 2014-01-30
The first screen says ~ "SMART HDD check detected an imminent failure" so the HDD is dying.

Then when I run Ubuntu from the DVD, I can access all the partitions normally, and all files seem to be in their place.

The folder /Users has three folders: Default, Public, Tanchistu.

Default and Public have the folders Desktop, Documents, Downloads, ... so on

Tanchistu has nothing, and when I click on properties it says "Contents: nothing"

I doubt I had a virus, and I doubt the drive has a physical problem reading files from that folder.

---

### Post by Tanchistu on 2014-01-30
When I am using "Disk Usage Analyzer" it says 461/624 GB used, but when I click on it, it only finds 44.8 GB.

It says that it encounters an error reading the "recycle bin", but nothing else.

---

