---
title: "Help understanding PI Ubuntu system backup please"
date: 2023-01-09
forum: General Help
---

### Post by bendy on 2023-01-09
Hi All

I am sure this has been asked elsewhere but I can't find it so asking for some help please.

I have a Pi4 with ubuntu 22.04 that has lots of system stuff on it (web, db, home bridge, Time Machine, etc). No real docs media etc. 

If my SD card goes bang I will be stuffed. Is there a tutorial on system backup and restore you know of that you could point me too?

I know I could shut the system down and clone the card but would prefer an overnight backup?

Any help gratefully received.

Thanks :-)

---

### Post by TheFu on 2023-01-09
> **bendy said:**
> Hi All

I am sure this has been asked elsewhere but I can't find it so asking for some help please.

I have a Pi4 with ubuntu 22.04 that has lots of system stuff on it (web, db, home bridge, Time Machine, etc). No real docs media etc. 

If my SD card goes bang I will be stuffed. Is there a tutorial on system backup and restore you know of that you could point me too?

I know I could shut the system down and clone the card but would prefer an overnight backup?

Any help gratefully received.

Thanks :-)

Anything THAT important shouldn't be put on flash storage.  With a Pi4, you can connect an SSD/HDD to it and use that for boot.  I don't know how, just know that other people do it.  Step 1, get your system off flash storage ... or run them inside a amd64/x86-64 system either as containers or VMs.

Server backups are harder and require intimate knowledge of the system to accomplish, unless you want to waste lots and lots of storage.  1 copy isn't a backup.  

If you want to leave the system running, then you'll need to use a volume manager to create clean backups.  You'll need to use something called "snapshots". Don't confuse those with the same term that most backup tool claim as snapshots.  They are nothing alike.  
[https://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html](https://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html) is the way to do LVM snapshots, but BTRFS and ZFS can do them as well.  If you don't have any of those, then you cannot accomplish a true "snapshot", regardless of what the backup tools claim.  In LVM, a snapshot freezes blocks of storage, so they won't change and provide a "name" which can be used to mount that "snapshot" read only while other parts of the system keep running full speed.  After you mount the snapshot readonly, you'll use whatever backup tool you like to to get the data to other storage.  Best of all this happens over the network using a different system and "pull" the backups to prevent malware on the clients from doing bad things to all that storage.

What you backup is up to you.  Beware that getting everything is usually a waste, since putting a base system back is trivial these days.  Exact commands for server backups is beyond these forums, but here are some simple, examples for typical desktop needs:
[Https://ubuntuforums.org/showthread.php?t=2482517&p=14125329#post14125329](Https://ubuntuforums.org/showthread.php?t=2482517&p=14125329#post14125329)
Here's my restore process: [Https://ubuntuforums.org/showthread.php?t=2474107&p=14091927#post14091927](Https://ubuntuforums.org/showthread.php?t=2474107&p=14091927#post14091927)

As with all things Unixy, there are 500+ different ways to accomplish the same things. Hopefully, others will chime in with their methods.  A few years ago, someone had a thread about using LVM and rdiff-backup, which is what I do.  

My scripts are fairly complex, since they are custom for my needs and have custom utilities included. There is also a non-standard ssh setup as I "pull" backups from the client systems, using a root-equiv userid to prevent the clients from having any access to the backup storage areas.

I've been told that doing what I do is beyond beginners and some intermediate admins.  For them, I'd suggest the shutdown any network services that would be writing to files, then use something like rdiff-backup, rsnapshot, rbackup or even back-in-time, to run their backups.

Whatever you do, setup "versioned" backups and avoid image-based backups. Images are just too wasteful and require shutting down the entire system, booting from alternate media, to create so corruption doesn't happen.

---

### Post by MAFoElffen on 2023-01-09
I have Raspberry Pi4. I was having troubles with my SD Cards intermittently. I changed to boot from SD to NVMe (via USB3). As mentioned above by TheFu...

But before that, I would pop the MicroSD card out and stick it in a card reader in my laptop. I would then dd copy and use compression to create a compressed image file of my MicroSD cards. With compression, they did not take much room.
```

datestamp=$(date '+%F'| sed 's/-//g' )
dd if=/dev/sdx | gz -c | dd of=~/backup-images/image$datestamp.img.gz

```
If I had a problem, I could quickly restore a recent image back onto a MicroSD card.

But since converting to booting from a hard drive, I have never had a problem since... (knocking on wood not to jinx that... LOL)

---

### Post by TheFu on 2023-01-09
I don't use Ubuntu on my r-pi systems. Just never moved off the custom image for OSMC (debian bullseye based), which I refresh about a year after every major OSMC/Kodi release.  Got burned with 1 major Kodi release upgrade that broke lots of addons. Even waiting a year, the last major upgrade lost some addons I'd been happily using for years like the ESPN3 addon. Sigh.

I only run OSMC and mpd on my raspberry pi computers.  Backup the settings for each using my normal rdiff-backup "pull" scripts, just like any other Linux system.  I don't have any data local on the pis.  All media is stored on the network managed by Jellyfin.  For music playback, the files are all nfs mounted.
As for storage on the Pi, I use Samsung PRO endurance microSD flash storage.  Previously, I had no-name storage which worked well enough for 3+ yrs, before it died.  Effectively, the backup script runs this:

```
sudo rdiff-backup --exclude-special-files \
        --exclude '**/.cache/mozilla' \
        --exclude '**/.cache/chromium' \
        --include /boot \
        --include /usr/local \
        --include /etc \
        --include /home \
        --include /root \
        --exclude '**' $RUSER@$REMOTE::/  "$TGT"

```
It is a base backup + home directories.  That is the exact line in my script. It "pulls" the data.

I pre-fill some system information in /root/backup/ to make restores easier:
```
# ls -al /root/backup/
total 56
drwx------ 2 root root  4096 Jan  2 12:03 .
drwx------ 4 root root  4096 Jan  2 12:02 ..
-rw-r--r-- 1 root root  6254 Jan  9 00:09 apt-mark.auto
-rw-r--r-- 1 root root  1003 Jan  9 00:09 apt-mark.manual
-rw-r--r-- 1 root root   198 Jan  9 00:09 blkid.txt
-rw-r--r-- 1 root root     0 Jan  9 00:09 crontab.osmc
-rw-r--r-- 1 root root     0 Jan  9 00:09 crontab.munin
-rw-r--r-- 1 root root     0 Jan  9 00:09 crontab.root
-rw-r--r-- 1 root root     0 Jan  9 00:09 crontab.www-data
-rw-r--r-- 1 root root   217 Jan  9 00:09 df.txt
-rw-r--r-- 1 root root 16486 Jan  9 00:09 dpkg.list
-rw-r--r-- 1 root root  1968 Jan  9 00:09 inxi.txt
-rw-r--r-- 1 root root   644 Jan  9 00:09 lsblk.txt
-rw-r--r-- 1 root root     0 Jan  9 00:09 lshw.list
-rw-r--r-- 1 root root     0 Jan  9 00:09 lvs.txt
-rw-r--r-- 1 root root     0 Jan  9 00:09 parted.txt
-rw-r--r-- 1 root root     0 Jan  9 00:09 pvs.txt
-rw-r--r-- 1 root root     0 Jan  9 00:09 vgs.txt
```

Zero length files mean either those tools aren't installed or there's nothing to report.  None of the LVM files have anything - no LVM used. Crontabs are pulled from /var/spool/ and are all empty, so any crontab entries are in /etc/.   The apt-mark.manual file is the most important besides all the data in /etc/ and /home/.

---

