---
title: "Better Backup method or program?"
date: 2019-06-20
forum: General Help
---

### Post by PDA1 on 2019-06-20
I need to backup my home folder to prepare against "the day of disaster".  I also want to do the backup in the easiest way as I'm no tech.  The backup will be made to a usb drive attached to my computer.

Which program would you recommend for doing a backup of my home folder?   I'm presently using Deja Dup but have read bad things about it.

Your suggestions or ideas would be much appreciated.

Thanks,

Peter (my name....today)

---

### Post by Bashing-om on 2019-06-20
PDA1; Hello 

My goto - routinely done: rsync !
```

rsync -aiv --exclude=".*" --exclude uwn /home/sysop/ /media/sysop/store/

```

here I do not backup any of the hidden 'dot' files or the 'uwn' directory.
See:
```

man rsync

```
for details.

[INDENT][INDENT]workie great, last ling time
[/INDENT][/INDENT]

---

### Post by cruzer001 on 2019-06-20
My go to app is also rsync, but I also like ease of use, so I just add a GUI front end to it, Grsync.

Its basic and simple way to do the job for the daily user.

You already have rsync its part of the standard install, just need to add grsync.
```
sudo apt install grsync
```
[http://www.opbyte.it/grsync/](http://www.opbyte.it/grsync/)

---

### Post by rbmorse on 2019-06-21
Another vote for grsync.  Has a "test" feature so you can fix mistakes before they happen!  

One of my personal life lessons is that if backups require _any_ active user participation they won't get done.  So, I've adopted a strategy that involves a dedicated internal hard drive (cheap these days) and one of the many "automatic transmission" versions of grsync called "backintime" (also in repository) that automagically performs the backup at user-defined intervals and intelligently manages the backup store.

 I still use grsync to do "spot" backups before making changes to the system configuration, or otherwise playing, "gee, I wonder what happens if I do this..."

Over the years, both grsync and backintime have saved my butt, and as recently as last weekend after foolishly playing with another distro (hanging head in shame) and getting my "/"s confused.  Had to wipe the drive and reinstall both Ubuntu and the applications I use which is trivial these days thanks to our dedicated developers. The last step was reinstalling grsync, entering the correct source/destination locations and clicking on the run session button to restore my user environment and data back to just the way they were before the stupids hit.

---

### Post by TheFu on 2019-06-21
Until around 2005, I used rsync, then I learned of a problem using it even with versioning using hardlinks.  Only the last mirror owner, group, permissions and ACLs are retained.  Over time, those can all change. Backup tools should retain those. Also, if the backup storage isn't using a Linux file system, all those permissions will be lost completely. Don't use NTFS or FAT-whatever on the backup storage.

I don't use GUI tools for backups for many reasons. Mainly because GUIs can't be automated via cron, and I want daily, versioned, backups to happen while I'm sleeping.  Deja Dup is based on duplicity.  Duplicity checks every box for what a great backup tool should do. EVERY SINGLE BOX.  But I don't use either, because 90% of the time, the backup I need to restore is the one from last night - or more likely, 1 file from last night.  Getting 1 file out of duplicity is a hassle. Duplicity can use NTFS/FAT-whatever for backup storage. There's an almost a good solution ... 

rdiff-backup.  The commands look almost identical to rsync.  It has include/exclude features.  The most recent backup looks like an rsync mirror. Getting that 1 file back from yesterday is just a copy.  But it also handled versioning and is extremely efficient with network bandwidth and storage of the different versions.  It also stores any permissions, owner, group, or ACL changes over time as part of the backup data.  While I've never used NTFS storage with rdiff-backup, it should work.  I wouldn't use it, however.

For a single user system, then root doesn't need to be used for backups of just the HOME directory. If there are multiple userids, then using sudo to run the backup for /home/ would be recommended.  If there are any large media files - like movies or TV shows in the HOME, I would move those to be somewhere else and back them up separately.  Any large files that don't change are best handled separately from normal settings and documents.

Anyways, the rdiff-backup commands you want are probably
```
sudo /usr/bin/rdiff-backup  --exclude-special-files \
           --include /home --exclude / --exclude /media \
           --exclude **/.local/share/Trash --exclude **/.cache \
           --exclude **/Cache \
            / /media/backup/storage/mount/location

```That should backup the stuff you want, but not the stuff you don't want.  Run that one time and you'll get a mirror.  Change 1 file in your HOME and run it again.  Only that 1 file gets included in the backups, but the mirror still looks like a mirror.

This will make new versions indefinitely so we need a way to remove really old versions of the backups.
```
 sudo /usr/bin/rdiff-backup --remove-older-than 180D \
          --force  /media/backup/storage/mount/location
```
That will remove any backups over 180 days old.  Most daily backups are only a few MB, so there isn't too much risk in filling the backup storage up unless it is almost full from the initial backup.  180 days might be too long for your needs.  60 days is usually long enough and doesn't take much storage, unless you accidentally leave different video files in your HOME from time to time.

If you backup just a few more things, you can make restoring to a new PC or wiping and reinstalling really easy.  
So, what else should you be backing up? It depends on how you use the PC. I backup these places on my desktop:```

--include /root
--include /etc
--include /usr/local
--include /home
```
I also backup the storage layout, crontab files used for automation, and list of all the manually installed packages.
```
 apt-mark showmanual | tee /root/apt-mark.manual
```
To restore the the packages, after you restore the settings in /etc/ and /root/, use```

 sudo apt-mark manual $(cat /root/apt-mark.manual)
 sudo apt-get -u dselect-upgrade
```
Depending on the amount of data in in /home, this process could take 30-45 minutes. When done, your files, your settings, all the programs are back configured just like they were previously.  Because you have versioned backups, you can get the information from last week, last month, 2 months ago. Support you get hit with a crypto-locker malware.  Without versioned backups, it won't look good. A simple mirror will be overwritten and all the data will be encrypted everywhere.

Back-In-Time is another solution, but it fails in the same way that rsync using hardlinks does. Underneath, BiT is doing that same process.

For the most secure backups, it is really best to have a backup server that "pulls" the backups from all the client machines.  "Pushing" or directly connected backup storage does leave the backup storage open to malware attacks.  Even if you don't use a backup server, having versioned backups of any sort can solve all sorts of common issues beyond malware. Unfortunately, it isn't just about a dead harddrive anymore or data corruption from bad programs that we need to protect against.

---

### Post by cruzer001 on 2019-06-21
> For a single user system, then root doesn't need to be used for backups of just the HOME directory.
+1 to that.  That's 90% of my backup plan these days.  Other considerations are backing up installed packages; installed 3rd party (PPAs) apps, a folder in home with my tweaks.  In a nutshell, everything important to me is located (copied) to home and then rsync (or whatever you decide to use) to a second drive.  Really important stuff also goes to the cloud.

---

### Post by HermanAB on 2019-06-22
OK, now that you have a backup going, you should read these, since after all of the above, you should now be able to understand it:
[https://www.nongnu.org/rdiff-backup/](https://www.nongnu.org/rdiff-backup/)
[http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

The original article by Mike Rubel describes how to keep three backups for the price of one, using a combination of hard links and rsync.  That idea then spawned the rsnapshot (pull) and diff-backup (push) scripts.

FWIIW, I have a little NUC with a 2TB disk that has all my music, movies and backups.  

On my MacBook, my backup script is directly based on Mike's and looks like this:
#! /bin/bash
# Rsync to Muzak 192.168.1.250 and keep 3 old hard linked copies.
# Assumes the public key is installed in /home/herman/.ssh
ssh herman@muzak "mv ~/Backups/Herman.3 ~/Backups/Herman.tmp"
ssh herman@muzak "mv ~/Backups/Herman.2 ~/Backups/Herman.3"
ssh herman@muzak "mv ~/Backups/Herman.1 ~/Backups/Herman.2"
ssh herman@muzak "mv ~/Backups/Herman.0 ~/Backups/Herman.1"
ssh herman@muzak "mv ~/Backups/Herman.tmp ~/Backups/Herman.0"
ssh herman@muzak "cp -al ~/Backups/Herman.1/. ~/Backups/Herman.0"  
rsync -avze ssh --progress --delete --max-size=20M --exclude "*Trash*" --exclude "*bak" \
 --exclude "*old" --exclude "*cache*" --exclude "*Cache*" --exclude "*iso" ~/ herman@muzak:~/Backups/Herman.0/ 

I simply run this little script whenever I feel like it.

---

### Post by uRock on 2019-06-22
I do it the easiest way possible. I drag and drop copies of files to an external drive as they're created. I only care about music, pictures, documents, and videos.

---

