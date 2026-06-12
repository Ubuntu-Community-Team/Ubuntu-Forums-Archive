---
title: "Can I Backup Entire Configuration To USB Stick? Does Size Matter?"
date: 2019-12-25
forum: General Help
---

### Post by soundchaser59 on 2019-12-25
I have a fresh install of Ubuntu 18.04 on a 300GB hdd. I have installed all the programs I want and everything is configured the way I like it. 
If the used space is only 200GB, does that mean I could backup my entire Ubuntu configuration - settings, installed apps, and personal files - to a usb stick that is only 256GB? 
If yes, what app do you prefer for doing that kind of backup? 

Or can I only back up my entire configuration to a destination that is equal or larger than the source?

---

### Post by Quarkrad on 2019-12-25
Be interesting to see how people respond - I think most people tend NOT to backup the whole OS but just your personal data.  That is because it only takes @20mins to re install the OS itself.  To make this possible , during the install process many install the OS in two separate sections called **/ **and another called **/home** (e.g. see [https://www.howtogeek.com/116742/how-to-create-a-separate-home-partition-after-installing-ubuntu/](https://www.howtogeek.com/116742/how-to-create-a-separate-home-partition-after-installing-ubuntu/)).  These separate areas can be on the same physical hard disk (e.g. in a laptop) or even on two different hard disks - doesn't really matter.  To backup your config a number of key folders also have to be backed up and we can help with these later. There are products like Clonezilla that can backup the whole disk to an image, allowing you to re-install that image in the event of something going wrong, but as said, many backup specific folders rather than everything (the backup is smaller /smarter and more efficient).  At this point it might be worth considering whether you want to backup your entire  OS or as I suspect the majority of people do, just backup the important personal data as leave the actual OS alone.

---

### Post by Artim on 2019-12-25
I use [systemback]("https://www.linuxbabe.com/ubuntu/install-systemback-ubuntu-18-04-bionic-18-10") to make a complete bootable copy of my installed system - applications, settings, bookmarks, passwords, and personal files.

---

### Post by jamescaan20 on 2019-12-25
Yes, software used 
[h=3]**Bacula**[B]
Amanda[/B][B]
Rsync[/B][B]
Time Vault[/B][B]
Clonezilla[/B][/h]

---

### Post by oldfred on 2019-12-25
I do not backup entire system as I can reinstall very quickly.
I do backup any system settings I change in /etc (mostly grub related), /home & export a list of installed applications into /home, so that is backed up. I also export various system outputs just to document configuration, but those are not required.

I copy data into another partition, but do not really consider that my backup as changes or history is not preserved. I do have backups of most critical data onto DVDs, onto flash drives & to my other other system in a less than totally organized fashion.
 
Better rules:
       Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992)
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)
More backup info from 1clue
[URL="https://ubuntuforums.org/showthread.php?t=2377810"]https://ubuntuforums.org/showthread.php?t=2377810

      [/URL]If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup) [URL="https://ubuntuforums.org/showthread.php?t=2377810"]
[/URL]

---

### Post by GhX6GZMB on 2019-12-25
I use two backup systems:
The primitive part is just backing up /home to save my work files.
For system configuration backup I use Timeshift (rsync-based). Works wonderfully and is very fast. By default, it does not include /root, as this should established with a reinstall. Otherwise all setups are kept and can be reestablished within minutes.
Timeshift is great when messing around, unsure about what you're doing. You're back to the previous setup very quickly.

---

### Post by soundchaser59 on 2019-12-26
Well, the reason I asked about the system configuration backup is because of what I do after I install from scratch. My machine is not new it is refurbished older hardware, so the main thing I have to do every install is jump thru a bunch of commands and apt stuff and updates just to get my wireless working again. That is where I have needed the most help from you experts! But then I change the petty stuff like screensavers, settings that are all based on preferences, browser settings and bookmarks, installing software like Libre Office, etc.etc.etc. In short I was hoping to have a way to backup/restore the basic OS and apps and settings (not including my personal files, those are the easy part of all this) so I don't have to reinstall and reconfigure all of that stuff from scratch after reinstalling the OS. If I could configure the freshly installed OS and software apps the way I want, without any personal files, and then back that up so that it is restorable, that would be awesome. My personal files can be restored any time from another USB stick, that's the easy part. 

I am especially interested in whether the backup app will balk if the backup medium (256GB usb stick) is smaller than the disk (300GB or 500GB hdd / ssd) on which the OS is installed......assuming the total OS + apps "image" is smaller than 256GB. For example, I've used Clonezilla before and iirc it will clone to a destination that is equal or bigger, but not to one that is smaller. I was hoping to use a usb stick so I could avoid having to open up the tower to mess with hard drives. IOW, have my working system on the internal hdd / ssd, and have my restorable backups on external medium like usb sticks.

---

### Post by GhX6GZMB on 2019-12-26
Once again, I've done this several times with Timeshift. It backs up everything except /home and /root by default.

First, get and save your UUIDs somewhere (sudo blkid)

Boot new from a DVD/USB, and do a 100% clean format/partition/reinstall. 

Set your partition UUIDs to the previous ones.

Install Timeshift and restore.

 Your system will be 100% like before, including programs, setups, configurations etc.

Concerning storage size: Timeshift backups and restores files, not bit-by-bit, so this is not an issue.

---

### Post by soundchaser59 on 2019-12-26
> **ml9104 said:**
> Once again, I've done this several times with Timeshift. It backs up everything except /home and /root by default.

First, get and save your UUIDs somewhere (sudo blkid)

Boot new from a DVD/USB, and do a 100% clean format/partition/reinstall. 

Set your partition UUIDs to the previous ones.

Install Timeshift and restore.

 Your system will be 100% like before, including programs, setups, configurations etc.

Concerning storage size: Timeshift backups and restores files, not bit-by-bit, so this is not an issue.

Ok, sorry I didn't fully grasp the meaning of your original post when you told me about Timeshift. That sounds like exactly the kind of "backup and recovery" I am aiming for. I will try it, assuming I can figure out exactly the steps to follow. I will be considering myself a Linux rookie for quite some time. I have background in Windows and SQL programming, but nothing dazzling, and I think of myself as more of a hack who gets things to work rather than a real professional programmer. It is only by divine grace that I manage to earn a paycheck doing it.

---

### Post by cmcanulty on 2019-12-26
I hope someone can explain how to set up timeshift to save all the pkgs and configs and no personal files. I tried it and found it quite complicated to set up the options. I use grsync to backup weekly all my files and certain settings but always end up have to reinstall several programs such as google earth, chrome, etc that aren't in the regular repositories.Thank you

---

### Post by ra7411 on 2019-12-26
It might be my 4 yr old usb 2.0 machine, but I can't even get large vid or aud files (~0.5 gb +) to copy then paste without time wasting failures using 16 or 32 gb usb sticks. 

I would use a regular sata hookup, sata-usb dock or usb hd.

For backups, I use qt5-fsarchiver for / (os) and Grsync for /home.   Both have saved my xxx a number of times over the last 4+ yrs of Ub use.

If your home files are small enough to not deter frequent non-incremental backups, then qt5-fsarchiver would be fine for backing up the os+home partition.

---

### Post by TheFu on 2019-12-26
Caution:  Often, flash storage needs to be formatted to use a Linux native file system for backups to work.  exFAT or FAT32 cannot be used.
With Linux, the backups are 50% file/directory data and 50% file/directory owners, groups, permissions, ACLs and perhaps xattrs. Systems files DEMAND that the correct ownership, group, permissions and any ACLs be correct. Some of these change over time, so any backup tool that doesn't handled versioning of that metadata too is not sufficient.

I've been using rdiff-backup for almost a decade. It isn't perfect but it does things that plain rsync and rsync+hardlink solutions fail to cover.

No backup solution should be considered complete until a full restore, onto new hardware, has been completed and tested. There are many subtle issues if you don't make a 100% bit-for-bit clone that can prevent a restore and ruin a day or week or month.

The links that oldfred posted has lists of the areas I definitely do and do not include in my backups.  Anyways, there's lots of reasonable advice, assuming you use a linux file system on the target storage.

---

### Post by ra7411 on 2019-12-26
>[COLOR=#000000]Caution: Often, flash storage needs to be formatted to use a Linux native file system for backups to work. exFAT or FAT32 cannot be used.[/COLOR]
[COLOR=#000000]With Linux, the backups are 50% file/directory data and 50% file/directory owners, groups, permissions, ACLs and perhaps xattrs. Systems files DEMAND that the correct ownership, group, permissions and any ACLs be correct. Some of these change over time, so any backup tool that doesn't handled versioning of that metadata too is not sufficient.<

Say, using Gparted, how should a usb stick drive be partitioned / formatted to avoid problems, particularly with large files?[/COLOR]

---

### Post by soundchaser59 on 2019-12-27
> **oldfred said:**
> [http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)  

Cloud? Could I, for example, back up to a personal web hosting folder?  [www.myhost.com/soundchaser59/mybackupdir ]("http://www.myhost.com/soundchaser59/mybackupdir/")

---

### Post by vidtek on 2019-12-27
I use a combination of weekly backups of my main ssd drive, a 250gb.  I have 2 identical ssd's for this.  It is important to have EXACTLY the same drive model numbers to get cloning to play nicely.

I dual boot Win 10 (windaz is used about once a month) and Kubuntu 18.04 with a home partition all on the same ssd and use a dual cloning dock (I use a Turbo Lepoard) as in the attached picture.  For a 250gb ssd it takes about 20 mins each week.
That backs up everything completely safely and gives me peace of mind with no worries about Windaz and office activation issues, driver wireless and video driver issues.

SSd's are so cheap now and the cloning dock when I bought it was about £25 from memory, they will probably be a lot cheaper now.

It has saved my bacon sooo many times when I have done foolish things!!:lolflag:

Edit: I also use one of these ssd easy eject hot swapping bays from Startech to make my life that bit easier, guess I'm just lazy.

---

### Post by ra7411 on 2019-12-27
> **soundchaser59 said:**
> Cloud? Could I, for example, back up to a personal web hosting folder?  [www.myhost.com/soundchaser59/mybackupdir ]("http://www.myhost.com/soundchaser59/mybackupdir/")

That depends on the size of your backup uploads, and your isp's upload rate - it might be way slower than its download rate.

---

### Post by TheFu on 2019-12-27
> **ra7411 said:**
> >[COLOR=#000000]Caution: Often, flash storage needs to be formatted to use a Linux native file system for backups to work. exFAT or FAT32 cannot be used.[/COLOR]
[COLOR=#000000]With Linux, the backups are 50% file/directory data and 50% file/directory owners, groups, permissions, ACLs and perhaps xattrs. Systems files DEMAND that the correct ownership, group, permissions and any ACLs be correct. Some of these change over time, so any backup tool that doesn't handled versioning of that metadata too is not sufficient.<

Say, using Gparted, how should a usb stick drive be partitioned / formatted to avoid problems, particularly with large files?[/COLOR]

exfat handles large files, but not permissions/ACLs/ownership.  Flash storage has a limited lifetime when it gets written over and over like daily backups would cause.  I've had named-brand flash storage fail after just over a year of daily use.  Flash storage doesn't last forever, though it is much more likely to appear that way when it is written much less.

Cheap flash storage might last much less than others.  A friend gave me some Microcenter "get 1 free" flash storage to exchange some files and it couldn't be read.  I formatted it exfat, tried again and failed.  Formatted it f2fs, tried again and it failed.  Formatted it fat32, tried and failed.  Tried it with different USB ports on the same machine each time  Failed.  Moved it to a different machine, failed.  He'd picked up the flash drive the prior month.

I would not use flash storage for backups.  I use spinning disk(s).
No way would I use cloudy storage for backups, but I suppose if you used a backup tool that used strong encryption, that could be OK.  There are lots of little things in backups that really shouldn't be public.

---

### Post by soundchaser59 on 2019-12-27
> **ra7411 said:**
> That depends on the size of your backup uploads, and your isp's upload rate - it might be way slower than its download rate.
The speeds are probably ok, 300mbps both up and down (fiber line to the house, basic tier service). 
But my web host might balk at storing a 200GB image, even if they like to say it's unlimited. I'll double check that, but a local "on site" backup would be better. Good point.

---

### Post by GhX6GZMB on 2019-12-27
What TheFu said!

Functioning Linux backup systems need a backup media with a Linux file system, preferably ext4. Rsync needs ext4, for instance.

Format your USB media with the following command;

     ```
sudo mkfs -t ext4 /dev/"yourdevice"
```

Then it should work with Timeshift or others.

---

### Post by soundchaser59 on 2019-12-27
> **ml9104 said:**
> What TheFu 

LOL!! At first glance my mind read it as "Whiskey Tango Foxtrot!" I've been watching too much Seal Team. 

I will try your tip, after I get my files and folders managed the way I want them. Thanks! 


> **ml9104 said:**
> Format your USB media with the following command;

```
sudo mkfs -t ext4 /dev/"yourdevice"
```

Then it should work with Timeshift or others.

---

### Post by TheFu on 2019-12-27
If you can live with the negatives of using pure rsync, fine.  I cannot.  I've been burned by ownership and permission changes happening and only the last backup/rsync values were available.  This happens with hardlink versioning that rsync supports too.  There are many "backup tools" that are based on rsync+hardlinks which all fail with this problem. Back-in-time is one.

Duplicity, duplicati, deja-dup which work the 1971 way of backups + have encryption don't have that problem.  On paper, the duplicity-based tools have everything anyone would want in a great backup solution.   All these tools are required to perform a restore.

rdiff-backup is lacking 2 aspects - encryption, but that is easily added on the target side with an encrypted file system. The other has a patch to correct - sparse file support.  You don't know you need sparse file support, until you do.  The most recent backup is just like an rsync mirror.  That means the restore is as easy as you want. No special tools needed.  Restoring 1 file is a copy. Getting a restore from 93 days ago is rdiff-backup -r 93D.

I've never used Timeshift. Don't know anything about it.  If it uses a GUI, I don't want it.  Most of my systems are servers without any GUI, so any GUI requirement is a liability.

Just for clarity.  EXT4 isn't **required**, but some Linux/Unix file system is.  There are lots of those, but in general, the viable choices are ext4, ZFS, and xfs. A case could be made to use ext3, ext2, jfs, or f2fs under very specific situations.  I use f2fs on flash storage, for example, but everywhere else I'll use ext4.  Personal preference.  

The only place to use NTFS is when hardware demand it. Have a hardware video recording device that only works with NTFS or fat32. The 1 disk used with that system is NTFS.

Anyway, those are my thoughts. Each location and setup will be a different so there are many other solutions. It is doubtful that my specific solution will fit everyone else or even most other situation.

Whatever anyone does, please, please, please, test a restore well before it is actually needed.

---

### Post by vidtek on 2019-12-28
The only 100% guaranteed perfect backup is a hardware clone as in my previous post.  Also that way the file system used is irrelevant.

If you really must use a software solution, try fsarchiver.   The cli version is in the repositories, but there is a QT4/5 version if required.  

There is also a stand-alone .iso which uses ubuntu,  I have a small 8gb pendrive with it on and it works really well.

It will also use any file system except BTRFS.   Newest version here:[https://sourceforge.net/projects/qt-fsarchiver/]("https://sourceforge.net/projects/qt-fsarchiver/")

Hope this helps.  Cheers, Tony.

---

### Post by GhX6GZMB on 2019-12-28
> **TheFu said:**
> 

I've never used Timeshift. Don't know anything about it.  If it uses a GUI, I don't want it.

Timeshift is a GUI on top of rsync and btrfs (free choice).

An experienced user would of course use these tools directly from the CLI, but for a beginner a bit of hand-holding is nice. The options for rsync are daunting, to say the least.

> **TheFu said:**
> 

[COLOR=#000000]Whatever anyone does, please, please, please, test a restore well before it is actually needed.[/COLOR]

Amen!

---

### Post by soundchaser59 on 2019-12-28
Plenty of tips and suggestions here to justify marking this thread solved. THANK YOU all for the assistance. 
I will experiment with some of these, but @vidtek may be right. A hardware clonezilla mission might be the most reliable way for me to go, given this old hardware + my inexperience with Linux.

---

