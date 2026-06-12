---
title: "Questions about basic rsync manual backups"
date: 2023-07-01
forum: General Help
---

### Post by AbleTassie on 2023-07-01
Hello all,

After reading several of the posts on the forum I am realizing the importance of backing up the Home Directory. And I have started to do this using rsync. I have read the 2021 article [How to backup your home directory in Linux]("https://www.pragmaticlinux.com/2021/05/how-to-backup-your-home-directory-in-linux/") which uses rsync and terminal commands to backup the home directory to a drive like a USB drive. The drive (in this case the usb drive is named "Backup") is manually mounted at /mntby using the Terminal command [COLOR=#c9211e]
sudo mount /dev/sdb1 /mnt/Backup [/COLOR]and the actual Home Directoty backup Terminal command is:   

 [COLOR=#ff0000]sudo rsync -a --info=progress2 --exclude="lost+found" --exclude=".cache" /home/ /mnt/Backup/[/COLOR] 
 
 
 I have done this type of back up using rsync twice now. The first time took a long time, maybe 30 minutes, to backup about 8 GB of Home Directory to the USB drive named "Backup."  The second time I backed up the Home Directory in the same way took a lot less time, about 7 minutes. I am assuming that this is because only files that have changed are automatically backed up with successive backups. **For reference, I have given the part of the Terminal outputs from the two backups underneath my username below.**

QUESTIONS: Is this correct that successive rsync backups automatically only backup files that have changed from the previous backup?

Is there any way to check the accuracy of the backed up Home Directory file on the usb drive, for example by comparing a SHA256SUM between the original Home Directory and the backed up Home Directory?

Thank you,

Able

                                  **Here is some of the Terminal Output from that first backup:**
 
able@able-x556uq:~$ sudo rsync -a --info=progress2 --exclude="lost+found" --exclude=".cache" /home/ /mnt/Backup/
 
6,685,257,700 99% 4.00MB/s 0:26:34 (xfr#6271, ir-chk=1003/8949)
 file has vanished: "/home/able/snap/firefox/common/.mozilla/firefox/ts4m1e23.default/storage/default/https+++mail.aol.com/cache/caches.sqlite-wal"
 file has vanished: "/home/able/snap/firefox/common/.mozilla/firefox/ts4m1e23.default/storage/default/https+++mail.aol.com/cache/context_open.marker"
 6,763,107,436 99% 3.76MB/s 0:28:36 (xfr#8136, to-chk=0/10951)  
 rsync warning: some files vanished before they could be transferred (code 24) at main.c(1338) [sender=3.2.7]

**Here is some of the Terminal Output from the second backup:**
 able@able-x556uq:~$ sudo rsync -a --info=progress2 --exclude="lost+found" --exclude=".cache" /home/ /mnt/Backup/
    256,933,510   3%  551.87kB/s    0:07:34 (xfr#1460, to-chk=0/11113)

---

### Post by tea for one on 2023-07-01
> **AbleTassie said:**
> QUESTIONS: Is this correct that successive rsync backups automatically only backup files that have changed from the previous backup?)
Yes, that is correct.
Your first backup of 30 mins sounds about right.
The second backup will only transfer files which have changed. Therefore, a much shorter process.
> In other words, rsync is a tool for efficiently copying and backing up data from one location (the source) to another (the destination). It is efficient because it only transfers files which are different between the source and destination directories
The above text is here [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

### Post by aljames2 on 2023-07-01
+1

I would just add that with your command, target will be larger than source over time without additional rsync options.  For example, with -a only, if you delete a file in source, rsyc will not delete that file in target, it keeps the old file & writes the changed version of the file to target.  This may be what you want.  If you want more of a synchronous relationship between source & target, then read about --delete options & --dry-run.

```
man rsync
```

If using --delete, include --dry-run at the end of the command first.  This will simulate the actual running of the command, displaying what &#8220;would have happened&#8221;.  Once you confirm that your command is correct, and you are happy with what the results will be, then simply remove the --dry-run to make the changes for real.

```
rsync -av --delete SOURCE TARGET --dry-run
```

Rsync with --delete can be dangerous if you are careless in writing your command. --dry-run gives you a second chance to fix it!

---

### Post by SeijiSensei on 2023-07-01
Rsync automatically checks the integrity of the files it creates. It checksums every file transferred. From the man page:
> Note that rsync always verifies that each transferred file was correctly reconstructed on the receiving side by checking a whole-file checksum that is generated as the file is transferred

You can force rsync to use checksums, rather than date/time modified, to determine whether a file should be transferred with the "--checksum" option. This will obviously take a much longer time as each source and destination file must be checksummed.

---

### Post by scpatl4now on 2023-07-01
I use Grsync which gives you a gui and I find that it is easier to use since it remembers your settings

---

### Post by HermanAB on 2023-07-01
Tip: With rsync, do not list the stuff you want to backup.  Rather include everything and exclude the crap you don't want to backup.  That results in a mostly maintenance free script.

---

### Post by oldfred on 2023-07-01
Note that rsync to one flash drive is just a copy. Better than nothing.
But if you change a file, and want the old version, it still is gone. If you use the delete parameter, it will also be deleted in your backup, but if not backup can grow a lot.
Old school was 3 copies, grandfather, father & son which you rotated around.

Many suggest/usr/bin/rdiff-backup
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006)

Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders) & 
[http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997](http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997) & 
[https://stackoverflow.com/questions/8270519/rsync-exclude-a-directory-but-include-a-subdirectory/37219769#37219769](https://stackoverflow.com/questions/8270519/rsync-exclude-a-directory-but-include-a-subdirectory/37219769#37219769)

---

### Post by AbleTassie on 2023-07-02
Thanks to everybody for their replies, I will look them over in detail and learn from them. I see that [**[COLOR=#000000]scpatl4now[/COLOR]**]("https://ubuntuforums.org/member.php?u=538883") uses Grsync which appears to be a GUI with rsync. I understand that there is another GUI for rsync that is popular, LuckyBackup. Does anybody have any comments about GUIs with rsync, including Grsync, LuckyBackup or others?

Thank you,

Able

---

### Post by The Cog on 2023-07-02
Just a couple of comments:

By default, rsync uses the file size and modification timestamp to determine whether a file has changed since its backup copy. As has been pointed out, the --checksum option also checksums the files if the stamp+size match.

Rsync does not necessarily checksum the disk content. "always verifies that each transferred file was correctly reconstructed on the receiving side" means in-memory checking, after a network transfer and before writing to disk. Normal disk writing routines are used to write to disk (i.e trust the OS to accurately write to disk what it is told to). Even the --checksum option (when used on a second verification run) might end up just checksumming what's in disk cache. I think un-mounting and re-mounting the backup drive should ensure that the disk cache is cleared.

---

### Post by TheFu on 2023-07-02
> **AbleTassie said:**
> Thanks to everybody for their replies, I will look them over in detail and learn from them. I see that [**[COLOR=#000000]scpatl4now[/COLOR]**]("https://ubuntuforums.org/member.php?u=538883") uses Grsync which appears to be a GUI with rsync. I understand that there is another GUI for rsync that is popular, LuckyBackup. Does anybody have any comments about GUIs with rsync, including Grsync, LuckyBackup or others?

Thank you,

Able

rsync has a number of flaws when it comes to backups, so all rsync-based tools inherit those flaws.  Mainly, only the last permissions, last owner, last group, are retained, assuming the target backup storage even supports those ideas.  Most flash storage is formatted as FAT32 or exFAT, so all the owner, group, permissions metadata are 100% lost.  That makes restoring anything outside a HOME directory almost useless.

Lots of backup tools use rsync + hardlinking.  This will provide versioned backups that are pretty clear to understand.  A Linux file system is required for the target storage, but again, the owner, group, and permissions are lost. Only the last backup version will have correct information.  80% of the time, that's fine.  But the other 20% of the time, you'll have a system that cannot be used after restore, which sorta defeats the entire reason for having backups ... unless you just want them to reference later, not use.  Getting the contents of /etc/ is pretty much mandatory to have any hope of putting files back with the correct users, groups, ACLs.

rsync is perfect when you want a mirror of all the files and they all have well-known permissions.  For something like media files - rsync is what I use. Works well.

For most small files on a system, like spreadsheets, documents, configs, we really need correct versioned backups, that are 100% automatic.  For this, I prefer rdiff-backup.  A very simple script to backup the minimal stuff is this:
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
That script can be used unchanged to get proper, versioned, backups, provided the target storage is a native Linux file system (ext4, zfs, f2fs, ....) and the script is run from root's crontab.
**rdiff-backup** is faster after the first backup than **rsync**.  That's because it retains the checksums for the target files between runs.  The first run would take the same time as an rsync does.  The script above keeps 120 days of versioned backups. That's a reasonable compromise. Longer is better for high risk systems.  90 days would be another reasonable time period.  How much you can keep depends on the contents of the source directories and the size of the target storage.  IME, 90 days uses about 1.3x more storage than the original files.  So, if you are backing up 10G, then for 90 days of versioned backups, you'd need about 13G of storage.  Seems like a bargain to me.  For my main desktop, here's the actual information:
```
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Sun Jul  2 00:06:23 2023         11.3 GB           11.3 GB   (current mirror)
Sat Jul  1 00:05:39 2023          926 KB           11.3 GB
Fri Jun 30 00:07:14 2023         2.32 MB           11.3 GB
Thu Jun 29 00:05:44 2023         6.33 MB           11.3 GB
...
Tue Mar  7 00:04:20 2023         1.18 MB           18.5 GB
Mon Mar  6 00:13:57 2023          608 KB           18.5 GB
Sun Mar  5 00:08:14 2023         80.2 KB           18.5 GB
Sat Mar  4 00:08:04 2023         5.59 MB           18.5 GB
```

On Mar 10, I left a few huge files in my HOME, by accident, so the amount backed up exploded.  Slowing, those files are working towards being removed in the backup storage. The problem could seem worse than it is if we used just percentages, but on the raw size of storage used, a few extra GB doesn't really matter.  Backups for all my systems are about 500GB today (I have lots and lots of systems).  They are on a 4TB HDD, so I have some room.
```
Filesystem                          Size  Used Avail Use% Mounted on
/dev/mapper/istar--8TB--B-lv5_back  3.4T  459G  2.8T  14% /d/b-D7

```

rdiff-backup isn't perfect. It doesn't do encryption, for example.  For that, the file system for the backups needs to be encrypted.  There are some backup tools that do encryption built in.  Duplicity, DejaDup, Duplicati are examples.  But those systems work in a very different way that rubs me wrong. I love that restoring a file or directory tree from rdiff-backup is just a cp or rsync. The most recent "backup" is stored like a simple rsync. That's nice and very useful.  But rdiff-backup addresses the issues that rsync versioning doesn't.

---

### Post by AbleTassie on 2023-07-04
Thanks to everybody for their replies and all the tips. I will likely incorporate many of these into my use of rsync as time goes on. I am really not very advanced, so at this point I don't use scripts. Although years ago I wrote programs in Fortran, C and pascal, so I am not afraid of scripts per se, it's just a question of time. Fortunately there is only one user, me so users and permissions are pretty simple. 

I will now mark this thread as SOLVED.

Thanks again for all the information.

Able

---

