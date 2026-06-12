---
title: "How do you backup your existing Ubuntu installation before updating?"
date: 2014-09-18
forum: General Help
---

### Post by Tom_Carr on 2014-09-18
On an update page it says

[COLOR=#333333][FONT=Ubuntu]"We recommend you backup your existing Ubuntu installation before updating."

But it does not tell me how to do it.  How do I do that?[/FONT][/COLOR]

---

### Post by oldfred on 2014-09-18
If anything there are too many different ways.

       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)
If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)

With Windows you might need a full image as it does not make it easy to reinstall. But with Linux you can easily reinstall and in some cases can do a new install in about the same time as a recovery of an image.
So from my home desktop I assume I will just do a new install and backup a list of installed apps, /home, my data which most of is not in /home and a few other things.

      
 Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

 Some files to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

 More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

I use rsync to copy data to another drive, use DVDs for most critical & changing info so I have copies in case I delete something. And copy some data now to flash drives. I use my own schedule on how often as I know most of my data can be relatively easily restored in a variety of ways.

I may convert from rsync to rdiff:

 Discussion of issues on rsycn bash file &  rdiff-backup  - TheFu
[http://ubuntuforums.org/showthread.php?t=2224428](http://ubuntuforums.org/showthread.php?t=2224428)

---

### Post by tgalati4 on 2014-09-18
If you have the disk space and the patience, it is perhaps better to setup dual-boot (or triple-boot) and keep your existing, working Ubuntu distro as a fallback that you can boot into.  Performing an in-place distribution upgrade will trash your current, working Ubuntu with a newer version that will probably need some (or a lot) of configuration.  My personal rule is:  "Never trash a working distro!"

Once you have your new partition/distro working for several months, then you can reclaim the space by backing up your personal data on the old partition and wiping it clean.  Then you can use the old partition as a backup for personal data, or as the future home of a newer distro, or something completely different.

---

### Post by Tom_Carr on 2014-09-18
> [COLOR=#000000]If you have the disk space and the patience, it is perhaps better to setup dual-boot (or triple-boot) and keep your existing, working Ubuntu distro as a fallback that you can boot into.[/COLOR]

How would I do that?  How  would I make an exact copy of my current system, and have it dual boot, so I can upgrade one and not the other?

---

