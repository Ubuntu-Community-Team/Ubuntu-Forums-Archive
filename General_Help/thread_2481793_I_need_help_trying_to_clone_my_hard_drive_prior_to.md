---
title: "I need help trying to clone my hard drive prior to migrating to 20.04(?)"
date: 2022-12-09
forum: General Help
---

### Post by rebeltaz on 2022-12-09
I don't  know where else to ask this, so I hope someone can help. 

I have found need for software that will not run with glibc 2.27 and apparently the only way I can do this is to move to 20.04 (I guess?). Anyone who know me knows I hate this and, again... here is just one more example of why.

I am trying to do a clone of my hard drive for the inevitable car wreck that is going to happen during this process. Little did I know that it would start so early in the process.... I created a USB boot drive with CloneZilla using unetbootin. I rebooted from the flash drive and have tried the default, from RAM disk and failsafe options but I keep getting the same error. It will say that it is trying to mount the root file system and then it will give me this error message about a dozen times before dropping to a command prompt: 

"couldn't mount because of unsupported optional features (2c0)"

I can boot the system just fine using that hard drive - I'm running it right now to write this - so I don't know why it can't mount it. 

Any help anyone can give me would be greatly appreciated!

---

### Post by Paddy Landau on 2022-12-09
I'm assuming that you currently use 18.04. While you are updating to 20.04, you might as well continue into 22.04, so that you have the latest LTS version.

As for cloning your drive, that's what I used to do, until I realised that cloning and restoring with CloneZilla takes longer than not bothering and installing from scratch. I install the latest LTS from scratch, thereby eliminating all upgrade problems (and there are quite a few, e.g. you have to update and re-enable all your additional PPAs), and then restore my data from my backups. It's much easier and cleaner.

However, if you really want to use CloneZilla, might I suggest that you give us some more information to help to diagnose the problem?

[LIST]
[*]Which drive is it complaining about: Your internal drive that you're trying to back up, or your external drive that you're trying to back up to?
[*]How are both of those drives formatted? Attach your backup drive, enter this command, and post your results here:
```
sudo parted --list
```
Be sure to indicate which drive you want to back up, and which is your target backup partition.
[*]Which version of Ubuntu do you currently have installed?
[*]Which CloneZilla did you download (stable or alternative_stable), and do you have the latest version?
[*]When you downloaded the CloneZilla ISO, did you check the SHA256 or SHA512 sums before writing it to your USB stick?
[/LIST]
You can also search Google for the error message "[COLOR=#000000]couldn't mount because of unsupported optional features (2c0)". There are several responses, which might give you a hint as to what's going on.[/COLOR]

---

### Post by Impavidus on 2022-12-09
> **Paddy Landau said:**
> I'm assuming that you currently use 18.04. While you are updating to 20.04, you might as well continue into 22.04, so that you have the latest LTS version.

That's to say, not a double release upgrade, but a fresh install of 22.04. You'll be fine for the next four years.

---

### Post by SeijiSensei on 2022-12-09
I use ddrescue to clone drives. It does a bit-for-bit copy of the source device. You can write the output to an iso file.

Debian, and thus Ubuntu, with its commitment to open source, requires you to install "gddrescue" because it comes from the GNU project.

sudo apt install gddrescue

---

### Post by Paddy Landau on 2022-12-09
> **SeijiSensei said:**
> I use ddrescue to clone drives. It does a bit-for-bit copy of the source device. You can write the output to an iso file.
The problem with this is that there's no compression, and unused space is also copied. CloneZilla copies only used space, and uses compression, thereby needing (usually) far less space in the backup than on the original disk.
> **SeijiSensei said:**
> Debian, and thus Ubuntu, with its commitment to open source, requires you to install "gddrescue" because it comes from the GNU project.
I can't comment on Debian, but Ubuntu doesn't require this. In fact, it isn't installed by default.

---

### Post by TheFu on 2022-12-09
> **Paddy Landau said:**
> The problem with this is that there's no compression, and unused space is also copied. CloneZilla copies only used space, and uses compression, thereby needing (usually) far less space in the backup than on the original disk.
 

fsarchiver is another option.  It full drive images or partition-level.  If the file system is known, then the image is not just compressed, but only the files are included, not empty space.  That means that at restore time, a smaller partition can be restored into.

Say / is 100G, but using only 35G of storage.  During the restore, the new partition can be sized as 36G and the restore will work perfect.

However, there is 1 critical thing with all these tools.  The source data cannot be mounted. This is to prevent corruption. For most people, the easy way to accomplish that is by booting from a flash ISO into the "Try Ubuntu" environment, temporarily installing whatever cloning tool you want, then running it to take the source --> target.  No intermediate step needed.

If you want an intermediate step, then something that will create a compressed image is needed.

However ... as your skill level with Linux increases, you'll come to realized that image-based clones are extremely inefficient. Hopefully, you'll see that file-based backups are crazy efficient, faster, more convenient and support having hundreds of versions of backups for less backup storage by far.  In my use, 90 days of daily backups need only 30% more storage than whatever the source size requires.  Say I have 10G of stuff to backup (I don't bother with the OS), then 90days of daily backups would be about 13G of storage.  That's it.  Further, each daily backup takes very little time, usually under 2 minutes.   Why wouldn't someone do this rather than the big production that creating an image requires?

A few system backups from last night:
```

=================
INFO: Backing up pihole ...
INFO: Backup Start:	2022-12-09-00:03:01
INFO:   Backup End:	2022-12-09-00:03:28
=================
INFO: Backing up spam1 ...
INFO: Backup Start:	2022-12-09-00:03:28
INFO:   Backup End:	2022-12-09-05:03:31
=================
INFO: Backing up wallabag ...
INFO: Backup Start:	2022-12-09-00:03:31
INFO:   Backup End:	2022-12-09-05:03:42
=================
INFO: Backing up vpn ...
INFO: Backup Start:	2022-12-09-00:03:42
INFO:   Backup End:	2022-12-09-00:03:44
=================
INFO: Backing up hadar ...
INFO: Backup Start:	2022-12-09-00:03:44
INFO:   Backup End:	2022-12-09-00:04:06
=================
INFO: Backing up regulus ...
INFO: Backup Start:	2022-12-09-00:04:06
INFO:   Backup End:	2022-12-09-00:05:00
=================
INFO: Backing up blog44 ...
INFO: Backup Start:	2022-12-09-00:05:00
INFO:   Backup End:	2022-12-09-00:05:19
=================
INFO: Backing up nextcloud ...
INFO: Backup Start:	2022-12-09-00:05:19
INFO:   Backup End:	2022-12-09-00:06:38
=================
INFO: Backing up osmc ...
INFO: Backup Start:	2022-12-09-00:06:38
INFO:   Backup End:	2022-12-09-00:07:24
```

So 9 systems got backed up from 00:03:00 --> 00:07:24 last night.  Most took under 1 minute.  BTW, some of those are high risk system and nearly 200 daily backups are retained.  The low-risk systems have 90 days of versioned backups.  BTW, I've used these backups a few times in 2022 for a few systems.  Just last week, I accidentally deleted a directory structure ... I was typing really fast.  Immediately, I knew about the mistake and copied the files back.  There are lots of tools that can accomplish this.  rdiff-backup, rsync+hardlinks (rsnapshot/rbackup), Back-In-Time are just a few).  For someone really new to Linux, Back-In-Time is probably the most intuitive. It uses hardlinks and manages the deletion of backup sets the farther away from "now" the backups are retained. It is pretty slick actually.

Image-based backups are too much hassle for me, take too long, use too much storage, and are out of date in a week.  But you'll need to decide that for yourself.

---

### Post by Paddy Landau on 2022-12-09
> **TheFu said:**
> … image-based clones are extremely inefficient. … file-based backups are crazy efficient, faster, more convenient and support having hundreds of versions of backups for less backup storage by far.
Yes! This is exactly my experience. I started with CloneZilla back in the Windows days. It took me some time to realise that Linux is far friendlier beast, and that using CloneZilla with Linux is like hammering in a nail with a steamroller, as well as wasting a huge amount of time and energy.

I used to use [rdiff-backup]("https://rdiff-backup.net/"), which is a great product, but I've now gravitated towards [BorgBackup]("https://www.borgbackup.org/"), which is far more efficient in both speed and storage use. Its one big flaw (the only one, I believe) is that it doesn't back up hard links.

For years, I have been using SpiderOakONE for my off-site (online) backups (SpiderOakONE also uses incremental backups with efficient space savings), but I shall almost certainly ultimately migrate to using BorgBackup. BorgBackup does have some GUI front-ends for the newbie, but I haven't tried them.

---

### Post by mIk3_08 on 2022-12-09
> **Paddy Landau said:**
> Yes! This is exactly my experience. I started with CloneZilla back in the Windows days. It took me some time to realise that Linux is far friendlier beast, and that using CloneZilla with Linux is like hammering in a nail with a steamroller, as well as wasting a huge amount of time and energy.
I used to use [rdiff-backup]("https://rdiff-backup.net/"), which is a great product, but I've now gravitated towards [BorgBackup]("https://www.borgbackup.org/"), which is far more efficient in both speed and storage use. Its one big flaw (the only one, I believe) is that it doesn't back up hard links.
For years, I have been using SpiderOakONE for my off-site (online) backups (SpiderOakONE also uses incremental backups with efficient space savings), but I shall almost certainly ultimately migrate to using BorgBackup. BorgBackup does have some GUI front-ends for the newbie, but I haven't tried them.
Oh! I'm not trying to depend clonezilla but the things that you have said about clonezilla, based on my experienced, 
I've using this tools for a decade now and it is exactly the  opposite things that happened to me. Maybe it depends on the users. 
Maybe I might be try to use those cloning tools you have mentioned above. I've already visited the site and it looks well and can be trusted. Thanks for sharing. Regards and cheers.

---

### Post by rebeltaz on 2022-12-09
> **Paddy Landau said:**
> I'm assuming that you currently use 18.04. While you are updating to 20.04, you might as well continue into 22.04, so that you have the latest LTS version.

As for cloning your drive, that's what I used to do, until I realised that cloning and restoring with CloneZilla takes longer than not bothering and installing from scratch. I install the latest LTS from scratch, thereby eliminating all upgrade problems (and there are quite a few, e.g. you have to update and re-enable all your additional PPAs), and then restore my data from my backups. It's much easier and cleaner.

However, if you really want to use CloneZilla, might I suggest that you give us some more information to help to diagnose the problem?

[LIST]
[*]Which drive is it complaining about: Your internal drive that you're trying to back up, or your external drive that you're trying to back up to?
[*]How are both of those drives formatted? Attach your backup drive, enter this command, and post your results here:
```
sudo parted --list
```
Be sure to indicate which drive you want to back up, and which is your target backup partition.
[*]Which version of Ubuntu do you currently have installed?
[*]Which CloneZilla did you download (stable or alternative_stable), and do you have the latest version?
[*]When you downloaded the CloneZilla ISO, did you check the SHA256 or SHA512 sums before writing it to your USB stick?
[/LIST]
You can also search Google for the error message "[COLOR=#000000]couldn't mount because of unsupported optional features (2c0)". There are several responses, which might give you a hint as to what's going on.[/COLOR]

After I read this, I got to thinking. I looked and it looks like unetbootin downloaded and installed v1.1.0-8. I have v2.6.0-37 downloaded already from a previous usage. I'll try that tonight and see if it works better. If not, I'll reply back with the requested info. 

As to doing a full install... I usually wind up having to do that anyway, but it's just such a pain. Like an idiot, I just keep hoping that this time.. this time the upgrade will go smoothly :)

---

### Post by rebeltaz on 2022-12-10
I just assumed that unetbootin would download the latest version of the iso. Not only wasn't it the latest version, but t wasn't even as new as the old version I already had! When I used my version, that went smoothly. Thank you for your help and I am sorry to ask such ignorant questions.

---

### Post by Paddy Landau on 2022-12-10
> **rebeltaz said:**
> I just assumed that unetbootin would download the latest version of the iso. Not only wasn't it the latest version, but t wasn't even as new as the old version I already had! When I used my version, that went smoothly. Thank you for your help and I am sorry to ask such ignorant questions.
I'm glad that you got it working.

Don't apologise: Ignorance is what this forum is here to solve! Remember in future that you need to give us full information to help you up front, such as versions and where you obtained your apps.  For example, sometimes there are renegade websites that serve out-of-date software, or worse.

Anyway, all is working, so have fun with 22.04.

---

