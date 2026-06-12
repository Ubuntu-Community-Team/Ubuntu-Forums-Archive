---
title: "How do I reinstall a full backup"
date: 2017-11-16
forum: General Help
---

### Post by notso23 on 2017-11-16
I was wondering how to do a complete reinstall of the system when it  crashes. I have read a lot of posts about it but I am more confused than  ever.
I recently went to upgrade my AMD drivers but it crashed and  went into a boot loop, just going around and around, and wouldn't boot  up at all. :(
I did have my personal stuff backed up on an external  hard drive, so it wasn't a total loss, but I still had to reinstall all  the programs etc that I like.

---

### Post by DuckHook on 2017-11-17
> **notso23 said:**
> I was wondering how to do a complete reinstall of the system when it  crashes. I have read a lot of posts about it but I am more confused than  ever.
I recently went to upgrade my AMD drivers but it crashed and  went into a boot loop, just going around and around, and wouldn't boot  up at all. :(
I did have my personal stuff backed up on an external  hard drive, so it wasn't a total loss, but I still had to reinstall all  the programs etc that I like.
There as many methods (and as many advocates for each of those methods) as there are flowers under the sun.

As a direct answer to your question, you can simply clone your drive. This will produce an exact copy of your main disk and can be done with dd (which is also called, tongue in cheek, "disk destroyer" for a reason) or Clonezilla. However, the drawbacks to this option quickly become apparent: they restore an image of your disk that was frozen in time. If your last clone was done some time ago, and your system has changed in the interim, then you lose all of those changes in a restore. It's therefore ungainly and inflexible and isn't often recommended.

You can also use an app like deja-dup, which is the default backup app in Ubuntu proper. You tell it to backup your whole system instead of just your /home directory and it should do as it's told. Because it is built as a backup app, it will handle things like rotating incremental backups, etc. However, the restore is rather involved because you must restore from a LiveUSB or similar workaround, and if you have a lot of incremental backups to restore, the process is tedious and can be error-prone. There are many apps like deja-dup. They all seek to paint a pretty front end on a set of utilities that already come bundled with a default Ubuntu install.

Then there's the method that I've settled on: using rsync to make a copy of my data only, but on a series of separate media that I physically rotate on a monthly basis. I'm not worried about my apps. If the worst happens, I'm content to reinstall the system followed by the apps. My experience is that I usually want to use the occasion of a reinstall to clean up my system and purge it of accumulated cruft anyway. Since I keep pretty good manual logs of all the apps I've installed (and their customizations and settings), it's not much more than an hour's job to get a clean and more efficient system. The data (everything in /home) is what's really important to me, and that's the only thing I need to back up.

The server gurus on this forum also swear by a combo of rsync and rdiff. Since my data accumulation isn't enterprise-level, I've never found the need for incremental backups. If you have this need, then you may wish to explore the rsync/rdiff combo.

It should be mentioned that rsync has a GUI front end called grsync. I've played around with it and can see its attraction for those who just can't stand the command line, but I don't use it.

There's no single backup app or strategy that stands heads and shoulders above all others. People's needs (and expertise) are so diverse that it's not possible to recommend any one default solution. For use of rsync, look at the link in my sig: BACKUP FIRST!

---

### Post by speartip on 2017-11-17
fsarchiver has always worked well for me.

---

### Post by oldfred on 2017-11-17
+1 on DuckHook's suggestions.

Some links:
 discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem) 


 Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)


TheFu is one if those that support many servers and suggests rdiff
Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992)

I am like DuckHook and a home user. But as home user am not as good as TheFu in regularly backing up. I do have backup on multiple drives, DVDs, and two locations. I use rsync to copy to another drive (TheFu  would not consider this a real backup, but it is a copy). I do add to my  backup script an export of all installed apps, and a run of  bootinfoscript which documents my partitions & configuration. And since copying to flash drive to move to my other location, I consider my multiple flash drives as another backup. If I manually edit something in /etc like my 40_custom, grub, or /etc/exports, or fstab, I manually copy into /home so that is backed up, but then do not back up all of /etc.

---

### Post by notso23 on 2017-11-17
Thank you for your replies.

If I do a complete backup to an external drive, can I then do the reinstall from boot to the external drive ... would that be correct?

---

### Post by oldfred on 2017-11-17
Almost all the install tools for the ISO to a flash drive or external drive totally erase the entire drive. So no, generally.

But I have grub installed to my smaller flash drives, and a full install to my larger flash drives. And have data partition separate for some or most of my data.
And I can using grub2's loopmount directly boot an ISO. But it is not the normal way most boot an installer.

---

### Post by notso23 on 2017-11-17
Thank you for your reply, I think I will be ok. 

Just have to work out how to update my AMD drivers without crashing the system, so I will read more about it. :p

---

### Post by 1clue on 2017-11-17
> **DuckHook said:**
> There as many methods (and as many advocates for each of those methods) as there are flowers under the sun.
...
Then there's the method that I've settled on: using rsync to make a copy of my data only, but on a series of separate media that I physically rotate on a monthly basis. I'm not worried about my apps. If the worst happens, I'm content to reinstall the system followed by the apps. My experience is that I usually want to use the occasion of a reinstall to clean up my system and purge it of accumulated cruft anyway. Since I keep pretty good manual logs of all the apps I've installed (and their customizations and settings), it's not much more than an hour's job to get a clean and more efficient system. The data (everything in /home) is what's really important to me, and that's the only thing I need to back up.


This one for me.

> 
There's no single backup app or strategy that stands heads and shoulders above all others. People's needs (and expertise) are so diverse that it's not possible to recommend any one default solution. For use of rsync, look at the link in my sig: BACKUP FIRST!

Absolutely correct.

I feel that it's important to note that rsync is not a backup strategy. It's a tool which can be and often is used in a backup strategy. DuckHook implements rotating media which is critical. If you backed up a week ago but that file got corrupted 2 weeks ago, and you're only using rsync to a single location, you're screwed.

Oldfred's "raid is not a backup" also resonates strongly for me. The purpose of RAID is to prevent device failure from causing downtime on mission-critical equipment. It's used way too often IMO.

Features of a good backup strategy:
[LIST=1]
[*]Only interesting information is backed up. System files and apps are not backed up, but a list of manually installed apps (the things I actually installed, not their dependencies) is included in the backup.
[*]There is a live, secured backup for convenience and rapid recovery of most accidents.
[*]It stores your important data in a time-ordered fashion. Meaning you can go back N backups and find out what your data looked on a particular date.
[*]Semi-automatic. It should be automatic enough that it doesn't require a huge amount of thought to do it, but manual enough that you review it regularly. To have fully automatic backups means that you back up data that was important 3 years ago but is no longer used, but forgot to add your currently important projects to the backup script.
[*]Protects from catastrophic acts of nature (fire, flood, earthquake, ...), physical theft/damage, electronic theft/damage, ransomware, malicious employees (family members?), accidental alteration/destruction of data.
[*]Uses common hardware and software which can be replaced from multiple vendors without affecting the usability of the backup.
[*]CAN BE RESTORED!
[/LIST]

I've used all sorts of backup media and backup software both privately and professionally. One day I had a failure and tried to restore my data from the tapes. The restore failed. It turns out all my backups had failed. Later after the disaster, I tried making a backup with a new tape, and that failed too. As far as I know that tape drive had never made a workable backup. The drive was no longer manufactured and this was way before craigslist or ebay came about. Since that day every backup strategy I've used relied on the most basic, standard mechanisms I can devise.

Currently:
[LIST=1]
[*]I have a central backup file server which does not accept connections from outside the LAN.
[LIST=1]
[*]It has an always-live **/backups** directory, which is secured per-user just like the original data was.
[LIST=1]
[*]One directory per host on the net, and then the files from that host go into the same directory within that host directory. **/backups/<hostname>/etc, /backups/<hostname>/home** for all straight copies.
[*]Database backups and other backups that can't be straight copies are sent to a special directory.  **/backups/<hostname>/mysqlbackups** instead of the actual usable database location.
[*]This serves as a hot backup for easy access in case somebody accidentally deleted something or a system went down.
[*]This section can use rsync, but only once per main backup cycle. Using it more often means it loses value as a backup because if you just synced an hour ago but deleted that file 2 hours ago you're screwed.
[/LIST]

[*]It has a slot for an ejectable SATA drive. This is just a standard internal 3.5" hard disk, which is the most common media I can come up with and, when you are careful about purchases, also very reliable and cheap.
[LIST=1|INDENT=1]
[*]This drive mounts to **/mnt/backups**
[/LIST]
[/LIST]

[*]Backup types I use:
[LIST=1]
[*]All backups are full backups. There  are no incremental backups. Incremental backups require that an older  series of backups exists and is readable. Full backups are faster to get  to the right place, and more reliable in that if any backup is bad then  ONLY that backup is bad.
[*]Long term backups are kept for a number of years.
[*]Short term backups are kept for a year or until the set has insufficient space for the next backup, whichever is longer.
[*]I don't use compression at all, or tar. Files are in their native format on an ext4 filesystem.
[LIST=1]
[*]This  means I can stick the drive into any Linux box and search for specific  files using any Linux tools, and get at that data as though it were a  normal disk.  Because it IS a normal disk.
[*]This means that  the most expensive time period -- when the system is broken -- the  system is the most reliable it can be, the most intuitive it can be to  restore.
[*]Data can intuitively be copied en masse, or selectively.
[*]Production files can be compared to backups intuitively, rapidly.
[/LIST]
[/LIST]

[*]I have a script on every machine for what I need to backup.
[LIST=1]
[*]It makes database backups or whatever other special backups are necessary locally.
[*]The backups are usually not compressed, but may be encrypted.
[*]It causes the remote backups directory to match the local files, meaning files deleted locally are also deleted on the backup directory.
[*]The installed package list goes into the backup, so I can start with a fresh install for that system.
[*]I backup configurations (/etc) but not binaries which exist in the repository.
[*]License keys for non-free software go into the backup. Some encryption keys go into a separate backup.
[*]Virtual machines:
[LIST=1]
[*]Virtual machine configuration files (machine name, how much RAM, etc) are backed up on the host.
[*]Each running guest is considered to be a machine on the network. As such it has its own backup plan just like any other computer.
[*]Backups or snapshots of a VM are backed up on the host machine.
[*]This strategy clearly won't work if you're always shutting down one machine and starting another. My VMs are all running unless they're only used occasionally. Occasional-use VMs are handled as data on the host.
[/LIST]
[/LIST]

[*]Backup media:
[LIST=1]
[*]Disks:
[LIST=1]
[*]Each disk is labeled with a backup set (week) number, drive within the set and date of purchase.
[LIST=1]
[*]Currently all my "sets" are one disk. It makes scripting easier.
[/LIST]

[*]I insert the disk, modify the contents and then eject. These are cheap  drives and will last until their size is considered ridiculously small.
[*]For home I can fit several backups on each drive.
[*]In any case the (mounted drive) directory structure is **/mnt/backups/yyyy-mm-dd/<hostname1>/...**
[LIST=1]
[*]The mount point of the cartridge is **/mnt/backups**.
[*]The date folder determines which backup set.
[/LIST]
[/LIST]

[*]Backup media sets:
[LIST=1|INDENT=1]
[*]I currently use 4 active backup media sets, 1 for each week.
[*]Whole-site backups happen on the 7th (week 1), 14th (week 2), 21st (week 3) and 28th (week 4).
[*]Remaining days go onto week 1's backup, as books close during and a few days after the month end and activity is high.
[*]Week 1 is a long-term backup.
[LIST=1]
[*]I fill the drive and then get a new drive, putting the full drive off-site.
[*]Each off-site storage location has its own long-term backup media, used once every N cycles, where N=number of sites.  See below.
[/LIST]

[*]Weeks 2-4 are short-term backups.
[LIST=1]
[*]These disks are recycled.
[*]I check the size of the current backup folder, and remove oldest backups until there's enough space on the drive.
[*]In the case of work (one backup per drive) I erase the disk and start over each time.
[*]If a short-term backup disk gets too old (based on the date of purchase I put on the label) I erase it and put it on the stack for long-term backups.
[/LIST]

[*]There are 3 off-site storage locations.
[LIST=1]
[*]Each time the backup set goes to the next location.
[*]This prevents a disaster (natural or human, intentional or not) at one location from losing my entire business or all of the backups. Long-term backups are alternated too.
[*]This prevents ransomware from working. The off-site backups are not hooked up to anything, they're just raw disks sitting in a safe place.
[/LIST]
[/LIST]
[/LIST]

[*]Backup to disk:


[LIST=1]
[*]**cp -rax /backups/* /mnt/backups/<yyyy-mm-dd>/**

[/LIST]
[/LIST]

---

### Post by paulparker2 on 2017-11-18
Well presented by  **1clue**  [URL="https://ubuntuforums.org/showthread.php?t=2377810&p=13712550#post13712550"]
[/URL]
BTW am NON-Technical... using linux over a decade.

Soon after started using computers (before linux), back-up applications often created problems,  so adopted habit of creating Archive COPYs of everything felt must be saved, they both stored and rotated, the copies of criticals elsewhere.proved their worth after arson destroyed our building.  .  

When an OS system fails often easier do clean re-install  [can re-use or import  **/home** from separate partition]  or just re-load from Archive COPY everything saved.    

Larger HardDrives make this easier, for critical and important.  


While non-technical, assist others with machines/OS's, usually first thing I do is COPY everything not hidden in their /home and mostly they surprised how much they thought lost was recovered. 

.

---

### Post by leunam12 on 2017-11-18
> **notso23 said:**
> I was wondering how to do a complete reinstall of the system when it  crashes. I have read a lot of posts about it but I am more confused than  ever.
I recently went to upgrade my AMD drivers but it crashed and  went into a boot loop, just going around and around, and wouldn't boot  up at all. :(
I did have my personal stuff backed up on an external  hard drive, so it wasn't a total loss, but I still had to reinstall all  the programs etc that I like.This is what I do: I keep / and /home on two different partitions. / is a small partition (25GB) which is way more than what I need to run my applications. /home is a large partition with all my data. I clone my / partition every week after updates using clonezilla and then I rsync my data to 2 different drives. If my system crashes I restore from the most recent system clone which takes only 5 minutes. Also, every time I am going to do something unusual (install experimental software, install third party drivers, compile a program from source, etc.) I clone my / partition, that way if something goes wrong I can go back with a simple restore that takes only a few minutes; pretty much like creating a restore point in Windows.

---

### Post by notso23 on 2017-11-18
Thank you all for your help and advice, so much to learn :)

---

### Post by Rick St. George on 2017-11-19
Hope this is not considered Hi-Jacking as it is same topic, perhaps same problem!

> **DuckHook said:**
>  For use of rsync, look at the link in my sig: BACKUP FIRST!

Followed your Link, and First, I tried this;

```

sudo mkdir /ZippedFiles
[sudo] password for stephen: 
stephen@stephen-evo-5723:~$ zip /ZippedFiles/archive.zip /home/stephen/ && rsync -av --delete /ZippedFiles/ /media/stephen/Data/Backups/
zip I/O error: Permission denied
zip error: Could not create output file (/ZippedFiles/archive.zip)
stephen@stephen-evo-5723:~$ sudo zip /ZippedFiles/archive.zip /home/stephen/ && rsync -av --delete /ZippedFiles/ /media/stephen/Data/Backups/
  adding: home/stephen/ (stored 0%)
sending incremental file list
./
archive.zip

sent 290 bytes  received 38 bytes  656.00 bytes/sec
total size is 176  speedup is 0.54

```

But then there was NOTHING in the Zip File, ONLY Dir Name.

So, after following advise here [https://www.linuxnix.com/linuxunix-zip-and-unzip-command-examples/](https://www.linuxnix.com/linuxunix-zip-and-unzip-command-examples/), added -r for recursive syntax, and received the following Error.

```

zip -r /ZippedFiles/archive.zip /home/stephen/ && rsync -av --delete /ZippedFiles/ /media/stephen/Data/Backups/
    zip warning: name not matched: /home/stephen/.kde/socket-stephen-evo-5723
    zip warning: name not matched: /home/stephen/.kde/tmp-stephen-evo-5723
    zip warning: name not matched: /home/stephen/.mozilla/firefox/jwwnl2w3.default/lock
    zip warning: name not matched: /home/stephen/tor-browser_en-US/Browser/.config/ibus/bus
    zip warning: name not matched: /home/stephen/.config/pulse/9db1ff253f2d2345979b028b548dcbfb-runtime
zip I/O error: Permission denied
zip error: Could not create output file (/ZippedFiles/archive.zip)

```

Can someone tell me what I'm doing Wrong???

[EDIT]  DUH! Forgot to add sudo.... Nevermind.

Thanks

---

