---
title: "Backup solution"
date: 2020-08-26
forum: General Help
---

### Post by xcfstarflight1 on 2020-08-26
Hi! How would you guys back up certain important folders and files and be sure that they are safe using Linux?
I was using onedrive before.
Some files that contain writing I want to keep are stored in folders that I want to back up regulary.
So this is a question divided into 3.
1. What backup solution should i use? Name of an online service or a program?
2. How do i set it up to backup intervaly? If possible
3. Can it take folders from wherever on the system?

Thanks! Sigurd, best regards!

---

### Post by Impavidus on 2020-08-26
I'm sure somebody will give you a long lecture on backups. But in short:
1: There are many backup solutions. Ready-made tools or you can write your own script. It depends also on your needs and resources. Have you got a dedicated backup server? Be careful with web services. If you value your privacy, encrypt your files before sending them to the cloud – and make sure you've got a backup of the encryption key somewhere safe, but not in the cloud.
2: You can schedule commands to run automatically at certain times using cron.
3: You can backup any directory you like. Many only backup their home directory. If the system breaks, you just reinstall.

---

### Post by xcfstarflight1 on 2020-08-26
Ok, But HOW? xD

---

### Post by ajgreeny on 2020-08-26
I use the simplest way, which some would argue is definitely not the best, but I regularly backup just my home, which incidentally already has copies of any system files I may have edited manually (not many but there's a few), using rsync to an external drive.

I have a separate /home partition so re-installing the root partition, ie the OS itself, is the work of a very little time, so I do not bother with backing up that, apart from those system files I already mentioned above.

---

### Post by GhX6GZMB on 2020-08-26
I've decided on a two-pronged approach:

1: I use Timeshift (rsync-based) for system backup, meaning all configuration and settings files in / , $HOME/Desktop and all the hidden files in $HOME. This has saved my life so many times (including complete reinstall/format) that I swear to it (manually setting up the machine to my liking after a crash otherwise takes days).

2: for /home I just do a brute force copy to an external disk. This is in no way the optimal solution, but I'm still looking for a sensible document management system for my user files.

I've chosen this way, so I only need to do a Timeshift backup when making changes to my system. Document backups I can do when I feel it's needed.

Probably too primitive for the experienced users here, but it works for me.

---

### Post by ra7411 on 2020-08-26
1] Grsync to daily incrementally back up my /home (my o/s has its own separate partition) to a separate backup HD on the computer.

2] If the building gets a lightening strike, that will nuke those drives, so every 3 weeks I Grsync backup my backup partition to an HD in a USB dock and that HD is then disconnected from any wiring. The house will have to burn down or something to destroy it.

3] Once a month I backup my o/s partition to avoid a re-install of o/s and apps. I use qt5-fsarchiver for the o/s backup.

4] I have a few things in /home that I would really hate to lose,  that is sent to a cloud site encrypted. That stuff is backed up in 3 places: the backup HD on the computer; the backup backup HD kept unconnected nearly all the time; on a cloud site.

---

### Post by xcfstarflight1 on 2020-08-27
but rsync cost money right?

---

### Post by xcfstarflight1 on 2020-08-27
The synsem needs to be ext or am i using fsarchiver wrong?

---

### Post by ajgreeny on 2020-08-27
No, rsync is part of the normal install, if I remember correctly, and costs nothing; if you want a GI for it install ***grsync*** but it's worth learning the syntax of the command line as well which is pretty simple.

To keep all file and folder permissions as they were, you should always backup to a Linux filesystem, ext4 being the most common nowadays.

---

### Post by HermanAB on 2020-08-27
If you have nothing better to do between 2 and 3 in the morning, then you can read this:
[https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html](https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html)

---

### Post by ra7411 on 2020-08-28
> **xcfstarflight1 said:**
> but rsync cost money right?

No rsync costs -0-, Grsync (rsync with a gui front) is also free and is downloadable from the regular Ubuntu software repository.

---

### Post by TheFu on 2020-08-28
[https://ubuntuforums.org/showthread.php?t=2447368&p=13973172#post13973172](https://ubuntuforums.org/showthread.php?t=2447368&p=13973172#post13973172)
One solution. All F/LOSS.   Versioned, daily, automatic, backups.  The last backup looks like an rsync mirror, which is very handy.  No funky, odd, file formats, efficient with storage, and very fast.

---

