---
title: "Is DD the best way to save a known good state of Ubuntu?"
date: 2023-04-03
forum: General Help
---

### Post by 777funk on 2023-04-03
I just had a problem where Timeshift had some kind of bug, froze, and corrupted a very complex fresh install of Ubuntu. I probably have 10 hours of software installation/configuration. So tears may be shed during the redo. I've never used Timeshift before and probably won't try it again.

In the past, I just DD'd to a spare hard drive and stashed that away for future use in the event of a failure. 

Is there a better way?

---

### Post by #&amp;thj^% on 2023-04-03
DD is one way, but so many others to consider as well:
> You might also want to check out these backup programs which will help you to make automated backups of your system:

    Clonezilla with Text GUI interface, backs up whole disks with boot sectors etc.

    Déjà Dup (Ubuntu's default desktop backup manager)

    TimeVault.

    FlyBack.

    Amanda.

    rsnapshot.

    storeBackup -- it has unique features. 
From here: [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
I use a combination of "zsys (ZFS SYStem integration)" snapper for BTRFS, these are now my only preferred file systems at install time.
You will get more from other users as well.

---

### Post by ne29914 on 2023-04-03
I use Timeshift for years, and it's never let me down. Never.
But there is a pitfall when you do a new installation and then try to restore from Timeshift. You'll have the same problem with dd and other packages as well, and it's got nothing to do with the backup program.

The issue arises when you do a reinstall and select the "format" option.
This assigns new UUIDs to your disk partitions. Your new system boots fine, everything is wonderful.
Then you do the Timeshift restore. This also contains essential system files that contain the _old_ UUIDs. Result: boot crash or no boot.
Two solutions:
1: do not format when doing the new installation. This is the simplest way.
2: rename the new partitions to have the old UUIDs before restoring. This is more complex, but necessary if you have a new HDD or PC.
(there is a third way by modifying the Timeshift backup files, but I can't recommend that unless you're real expert).

---

### Post by TheFu on 2023-04-03
> **777funk said:**
> I just had a problem where Timeshift had some kind of bug, froze, and corrupted a very complex fresh install of Ubuntu. I probably have 10 hours of software installation/configuration. So tears may be shed during the redo. I've never used Timeshift before and probably won't try it again.

In the past, I just DD'd to a spare hard drive and stashed that away for future use in the event of a failure. 

Is there a better way?

Are the configurations for a single userid or for the entire system?  All individual settings are stored inside your HOME directory, so you can do a fresh install and just restore the HOME to get all your settings back.  I understand that Timeshift doesn't usually backup a HOME directory, so all that would be lost.

For most desktops, no changes should be made outside of each user's HOME, typically in /home/{username}
A very simple backup script, which should work for most people on desktops would be:
```
#!/bin/bash

TGT=/Backups
DAYS=120

# Run backups and commands as root to maintain permissions, owners, groups, ACLs

# Ensure directories exist
mkdir -p /root/backups 

# check that backup target storage is mounted; many different methods exist
#  * check the mount for the expected directory
#  * look for a "not-mounted" file that exists under the mount point

# Save list of manually installed packages - to be restored later
# Be certain the redirected file is part of your include backup locations
/usr/bin/apt-mark showauto > /root/backups/apt-mark.auto
/usr/bin/apt-mark showmanual > /root/backups/apt-mark.manual

# Local Backups; all backups need to run as root, to capture file metadata
/usr/bin/rdiff-backup \
        --exclude-sockets --exclude-device-files --exclude-fifos \
        --exclude '**/.cache'  --exclude "$TGT" \
        --include /usr/local   --include /etc  \
        --include /root        --include /home \
        --exclude '**'   /       "$TGT"

# Trim old backups from long ago
/usr/bin/rdiff-backup  --remove-older-than "$DAYS"  --force "$TGT"

```
Change the TGT to a different, external, mounted disk with a Linux native file system.
Run that script as root - weekly or daily.  It will get everything that most desktop users need. The first backup will take as long as a typical rsync will, but the next day and every day thereafter it will likely be minutes. 90 days of versioned backups use about 1.2-1.3x the storage of the original files.  I keep 120 days of versioned backups by default - more for higher risk systems - some that are very high risk, but don't have any data I'm keeping over a year of versioned backups. They are just processing emails or a web reverse proxy with no data, so the backups are tiny.

My restore process begins with doing a fresh OS install using a standard Ubuntu flavor, minimal install. Usually takes 9-14 minutes.  Why backup stuff that is easily replaced?  [Https://ubuntuforums.org/showthread.php?t=2474107&p=14091927#post14091927](Https://ubuntuforums.org/showthread.php?t=2474107&p=14091927#post14091927) has a detailed guide for restores.

I kept the script simple on purpose. There are some improvements that should be made, like validating the TGT is mounted and available.

If you are only interested in 1 copy, use **ddrescue** over **dd**.  Both have flaws, since they get all the unused space too.  If you are on a spinning HDD, writing x00 to all the empty space will drastically aid compression utilities, so the image.gz can be significantly smaller if the entire drive or partition(s) have free space.  For SSDs, writing zeros to empty space would be bad - reducing the lifespan for the drive. Hopefully, the SSD controller will be smart enough not to provide bogus data on unused blocks, but I don't know if that works that way or if it does, which SSD models do it.

Much more efficient (space and time) to use file-based backups.  rdiff-backup is very efficient.  Best of all, the most recent backup appears like an rsync mirror, so to restore a file from yesterday is just a "copy".

Of course, there are lots and lots of opinions about backups and which tools are the best. Only you can decide.

---

### Post by sgage on 2023-04-03
I have always simply used dd. I run it to image a nice functional installation from time to time. I always run it from a different partition, so the that system I am imaging is in a shut down state. You can also do it from a USB boot. I have never had a problem restoring an image. 

If you are dual booting with Windows, Macrium Reflect works fine on Linux partitions. It's a lot faster than dd and does compression. But dd, for me, is simple, understandable, and never fails. I've had problems with all the others.

---

### Post by #&amp;thj^% on 2023-04-03
> **sgage said:**
>  But dd, for me, is simple, understandable, and never fails. I've had problems with all the others.

I first picked DD up from you in the Development sub forums, and use it still for other things I do.
TheFu took me to new heights with snapshots over the years.(TL:dr)

---

### Post by 777funk on 2023-04-03
> **TheFu said:**
> Are the configurations for a single userid or for the entire system?  All individual settings are stored inside your HOME directory, so you can do a fresh install and just restore the HOME to get all your settings back.  I understand that Timeshift doesn't usually backup a HOME directory, so all that would be lost.

For most desktops, no changes should be made outside of each user's HOME, typically in /home/{username}
A very simple backup script, which should work for most people on desktops would be:
```
#!/bin/bash

TGT=/Backups
DAYS=120

# Run backups and commands as root to maintain permissions, owners, groups, ACLs

# Ensure directories exist
mkdir -p /root/backups 

# check that backup target storage is mounted; many different methods exist
#  * check the mount for the expected directory
#  * look for a "not-mounted" file that exists under the mount point

# Save list of manually installed packages - to be restored later
# Be certain the redirected file is part of your include backup locations
/usr/bin/apt-mark showauto > /root/backups/apt-mark.auto
/usr/bin/apt-mark showmanual > /root/backups/apt-mark.manual

# Local Backups; all backups need to run as root, to capture file metadata
/usr/bin/rdiff-backup \
        --exclude-sockets --exclude-device-files --exclude-fifos \
        --exclude '**/.cache'  --exclude "$TGT" \
        --include /usr/local   --include /etc  \
        --include /root        --include /home \
        --exclude '**'   /       "$TGT"

# Trim old backups from long ago
/usr/bin/rdiff-backup  --remove-older-than "$DAYS"  --force "$TGT"

```
Change the TGT to a different, external, mounted disk with a Linux native file system.
Run that script as root - weekly or daily.  It will get everything that most desktop users need. The first backup will take as long as a typical rsync will, but the next day and every day thereafter it will likely be minutes. 90 days of versioned backups use about 1.2-1.3x the storage of the original files.  I keep 120 days of versioned backups by default - more for higher risk systems - some that are very high risk, but don't have any data I'm keeping over a year of versioned backups. They are just processing emails or a web reverse proxy with no data, so the backups are tiny.

My restore process begins with doing a fresh OS install using a standard Ubuntu flavor, minimal install. Usually takes 9-14 minutes.  Why backup stuff that is easily replaced?  [Https://ubuntuforums.org/showthread.php?t=2474107&p=14091927#post14091927](Https://ubuntuforums.org/showthread.php?t=2474107&p=14091927#post14091927) has a detailed guide for restores.

I kept the script simple on purpose. There are some improvements that should be made, like validating the TGT is mounted and available.

If you are only interested in 1 copy, use **ddrescue** over **dd**.  Both have flaws, since they get all the unused space too.  If you are on a spinning HDD, writing x00 to all the empty space will drastically aid compression utilities, so the image.gz can be significantly smaller if the entire drive or partition(s) have free space.  For SSDs, writing zeros to empty space would be bad - reducing the lifespan for the drive. Hopefully, the SSD controller will be smart enough not to provide bogus data on unused blocks, but I don't know if that works that way or if it does, which SSD models do it.

Much more efficient (space and time) to use file-based backups.  rdiff-backup is very efficient.  Best of all, the most recent backup appears like an rsync mirror, so to restore a file from yesterday is just a "copy".

Of course, there are lots and lots of opinions about backups and which tools are the best. Only you can decide.

Makes perfect sense and thank you! I have made a habit of DD since I've dual booted for a while and it's an easy way to duplicated all partitions. 

So... does backing up the home directory also restore programs and settings? I know there is some data in /usr etc that I've seen some apps pull from.

---

### Post by TheFu on 2023-04-04
> **777funk said:**
> Makes perfect sense and thank you! I have made a habit of DD since I've dual booted for a while and it's an easy way to duplicated all partitions. 

So... does backing up the home directory also restore programs and settings? I know there is some data in /usr etc that I've seen some apps pull from.

If you have a list of installed applications (like apt-mark in the script I posted does), then you include that/those lists in your backups, then they can be fed into APT on the new/restored system as the LAST STEP.

There shouldn't be any files that were custom under /usr/   except in /usr/local/, which is why /usr/local/ is included in the list of directories to be backed up.  Everything else under /usr/ outside that specific directory should be stock, as the package installs it.  System settings belong in /etc/.

There are standards for where things belong.  Ubuntu generally follows them ... except their snap packages break all sorts of those rules. Don't ask me why they chose to do that.  If you specifically know of other places you'd like to backup, the script is pretty clear ... only touch the --include stuff. Leave everything else alone.  Order matters, so put your extra includes, if you have any, into the middle of the other includes already there.  This is **not** a beginner script. You are expected to look up any options you don't understand in the manpages and you should practice doing backups and restores to ensure there isn't something funky about your system being missed.  

The stuff that gets included will make restoring a complete system possible in about 45 min with practice. Some of the the things backed up are purely for reference. For example, blindly restoring everything in /etc/ will break a system that was just installed, but there are files in there that are extremely useful for reference.  It is so small that grabbing everything is worthwhile and fast.  The files in there seldom change, so they don't really add to the space needed for backups even over long periods.  Whenever I edit any files under /etc/, I add a tag comment that can be searched so I know the file was manually modified. At restore time, I search for those tags, see what they are and decide if those manual changes are needed on the new system (or not).  Nothing replaces a smart admin.

For example, Timeshift misses some pretty important locations, IMHO.  OTOH, dd/ddrescue and all imaging tools are so very wasteful, for very little gain and ZERO flexibility.  File-based backups make for extremely flexible restore possibilities.  I've completely changed the file systems from EXT4 to ZFS.  I've migrated from 16.04 ---> 20.04 using this backup-restore method.  With images, that isn't possible without keeping all the OS cruft.

Backups aren't just for a failed HDD. They should be used for hundreds of other possible issues too.  Versioned backups are my #1 security tool. Without versioning, it is impossible to store enough copies to track when malware was first installed.  With crypto-locker malware, I'll see my backups double overnight and take much longer.  With image-based backups, first they are too difficult that nobody will do them often enough.

My backup for about 10 systems begins a little after midnight, local time.  For my desktop, 
```
=================
INFO: Backing up deneb ...
================= 
INFO: Running sudo rdiff-backup  --exclude-sockets --exclude-device-files --exclude-fifos ...
INFO: Removing backups older than 120D
No increments older than Sun Dec  4 23:05:23 2022 found, exiting.
INFO: Post-Backup-Cleanup() 

INFO: Backup Start:	2023-04-04-00:04:40
INFO:   Backup End:	2023-04-04-00:05:23
=================
Done.
```
That entire backup, with the system running, took under 1 minute.  It contains everything I need to recreate "my system" in less than 45 minutes, starting from a fresh install. Also, I "pull"ed the backup over the network to a different system. The desktop cannot directly access any of the backup storage, so malware on a client desktop system cannot harm the backup storage.

Tomorrow morning, I'll get an email which the start/end times and how much data was written.  If it is 20G, then I know some bad malware happened today, but with 1 minute needed to backup all the changed data since last night, I doubt it will be more than a few MB.

Home directories contain your personal settings and personal data, unless you go out of your way to put those somewhere else.

---

### Post by HermanAB on 2023-04-04
In my experience it is best to do development work in a VM, leaving the host alone.  Backing up a VM is easy- just make a zip archive of it.

---

