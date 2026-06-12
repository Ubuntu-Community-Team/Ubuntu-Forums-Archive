---
title: "Thoughts/ideas on backing up my system"
date: 2016-07-08
forum: General Help
---

### Post by RadioAdi on 2016-07-08
Hi, 

As I have installed software on my laptop over the years and customised my OS the idea of a hardware or firmware failure leading me to have to setup and reinstall everything from scratch is making me increasingly anxious. 

I have a NAS with two drives in a RAID configuration so my data is not the main concern. 

I see two solutions to this:

1. Clone the OS. My concern with this approach is a) it strikes me are quite a tricky procedure which I would have to do regularly b) I will eventually have to replace my laptop with a newer model, I suspect it will not be possible/advisable to load a ISO of an operation system configured for certain hardware to a different machine, but then I may be wrong.  

2. Build a desktop machine for use as server and remote into this from my laptop like a client. Of course the server could fail but I suspect it will be easier to repair or replace/upgrade components without having to replace the entire machine. Downside to this of course is the cost of hardware and energy cost of running the server constantly, and perhaps some decreased performance and the inconvenience of working via remote desktop. 

Anybody have any thoughts on the above? Anybody have any better solutions?

Thanks

---

### Post by DuckHook on 2016-07-08
A number of observations that are purely my opinion:

[LIST=1]
[*]Do not be too sure of your data integrity in a RAID configuration. RAID is not meant to be a backup strategy but a constant availability strategy. For backups, nothing will replace having an image of your data stored offline&#8213;preferably off-site.
[*]Cloning the OS is done all the time by many forum members, but I find the drawbacks outweigh the benefits, so I don't do it. I find that it is too easy in Ubuntu to just reinstall the system and the apps, so a clone is more trouble than it is worth to me. From the practical perspective, a reinstall of the system cleans it of the cruft that I have accumulated from months of experimentation (installing, then purging), and it is often such practices that create not immediate but latent problems. A clone could simply drag those latent problems back into your new system disk.
[*]Based on your description, a remote desktop solution seems overkill for your purposes. It also creates other problems, since remote desktops must open ports in your firewall in order to handshake and exchange data. Not least, such a setup still risks your OS since it is just as easy for your server to go down as your laptop, so you haven't really gained anything. And no, server components are not easier to get than laptop.
[/LIST]
If my own practice might serve as a guide:
I notarize onto a primitive text log each step that I take after a new install to add apps and customize. This allows me to not only track my customizations, but to easily install the same packages onto any other machine. Most of all, it serves as a permanent guideline for me in case I forget what has been installed, and that I can back-reference to see what packages I may have once installed but are no longer needed.

---

### Post by oldfred on 2016-07-08
Business or personal? Or how often do you want to backup?

My methods, which may not apply:
My system now is just my wife & I and most recent data I can recreate pretty easily. And I do not have a lot of data.
So I copy some data from one drive to another, and most important data like photos of grandkids are archived to DVDs regularly. Some is copied to flash drives and other system I have. A real mishmash. 

 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery) 

I do not believe in backing up Ubuntu. And now can restore it in about an hour or less if required.
I do have flash drives with current LTS version, so I can reinstall it, but also have it installed on other systems. And every hard drive and some larger flash drives have a version of Ubuntu on them.
I do backup list of installed applications & /home. I link data folders to data partition(s) on other drives. And regularly install next Ubuntu version to test my install procedures, but have not totally erased my main working install to see if I can restore it. And I still have my working 14.04 install on same SSD as my new 16.04 install. The 14.04 install will probably get overwritten with 18.04, current list of apps in 16.04 installed and data relinked via a small script.
I use rsync to back up my data, to other drives & flash drives.

      
 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders) 
    
Some other posts with good advice.

 Discussion of issues on rsync bash file &  rdiff-backup  - TheFu
[http://ubuntuforums.org/showthread.php?t=2224428](http://ubuntuforums.org/showthread.php?t=2224428)
[http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/)
Sample rdiff file by TheFu
[http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880](http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880)
[http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use](http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use)

---

### Post by DuckHook on 2016-07-08
^ +1

... these are almost the identical steps that I do. But then, both oldfred and I are retired, lots of time on our hands, into rehabilitating salvaged systems, and just love fooling around with this stuff (Linux & Ubuntu). Your mileage may vary.

---

### Post by RadioAdi on 2016-07-09
Thanks guys, will digest this properly later and be back with any questions.

---

