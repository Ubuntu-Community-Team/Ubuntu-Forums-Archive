---
title: "Deja Dup won't acknowledge free space"
date: 2018-10-26
forum: General Help
---

### Post by JamButty on 2018-10-26
I use Deja Dup to backup to a separate partition. Although it is supposed to clear old files as space runs out, it never does and I must delete old files when it gets full. That is ok, I am used to it, but I just did this and backup seems stuck in the prior error state. It will not recognize that there is 2x as much free space as needed for a full backup (97.8 GB free, ~37GB needed). Reboot did nothing. Emptying trash folder did nothing. Deleting trash folder and re-establishing it by writing a test file to the partition and deleting it did not help. It always says
> Backup location is too small.  Try using one with more space.
The only thing on the partition is the trash folder with tiny test file and the lost+found, which I do not have permission to touch.
I am out of guesses.

---

### Post by TheFu on 2018-10-26
Is the underlying file system btrfs?  df -Th
Are there plenty of inodes available?  df -i

---

### Post by JamButty on 2018-10-26
Backup partition (SDA8) is ext4. Dunno what inodes are, but 6M seems like plenty.
```
df -Th
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  5.8G     0  5.8G   0% /dev
tmpfs          tmpfs     1.2G  1.9M  1.2G   1% /run
/dev/sda6      ext4      789G  175G  574G  24% /
tmpfs          tmpfs     5.9G   26M  5.8G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     5.9G     0  5.9G   0% /sys/fs/cgroup
/dev/sda1      vfat      496M   31M  466M   7% /boot/efi
tmpfs          tmpfs     1.2G   16K  1.2G   1% /run/user/120
tmpfs          tmpfs     1.2G   40K  1.2G   1% /run/user/1000
==============
/dev/sda8      ext4       96G   60M   92G   1% /media/homer/Backups
===========
homer@homer-Inspiron-3847:~$ df -i
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
udev            1519016    585  1518431    1% /dev
tmpfs           1526578   1071  1525507    1% /run
/dev/sda6      52551680 233325 52318355    1% /
tmpfs           1526578     67  1526511    1% /dev/shm
tmpfs           1526578      5  1526573    1% /run/lock
tmpfs           1526578     18  1526560    1% /sys/fs/cgroup
/dev/sda1             0      0        0     - /boot/efi
tmpfs           1526578     24  1526554    1% /run/user/120
tmpfs           1526578     35  1526543    1% /run/user/1000
=================
/dev/sda8       6406144     16  6406128    1% /media/homer/Backups
===================

```

---

### Post by TheFu on 2018-10-26
Please edit the post and use "code tags" ... quote tags make it hard/impossible to read.

But I was just guessing at some simple issues - limited storage and a file system that lies about available storage. Guessing those aren't an issue?

BTW, none of the "loop" things are useful.  Removing them would be helpful to let someone who may have other ideas concentrate on what is important.

Is  /media/homer/Backups where you intend to place the backups?  Are the directory permissions ok?

---

### Post by JamButty on 2018-10-26
yes to both. "homer"=root. I have been using that backup partition a couple of years now. I thought I had permission problems once a year ago, but that turned out to be the problem that deja dup cannot mount that partition by itself, I have to do it through "files" first. I am baffled as nothing unusual happened. I have to delete all the backup files and do a new full backup every time that partition fills, which is a few times a year and it has never been a problem before.

```
 ll /media/homer/Backups
total 236
drwx------  4 homer homer 212992 Oct 26 09:56 ./
drwxr-x---+ 3 root  root    4096 Oct 26 12:07 ../
drwx------  2 root  root   16384 Oct 31  2016 lost+found/
drwx------  4 homer homer   4096 Oct 26 09:56 .Trash-1000/


```

---

### Post by TheFu on 2018-10-26
You should remove everything in /media/homer/Backups/.Tra*   and don't use a GUI to do it.  Use the shell/CLI/terminal.
I suspect that will solve the out-of-storage problem.  Using a GUI has some problems.

It would be better if you didn't use the GUI to mount that storage.  Using the GUI uses GVFS which is inferior to real mounts in so many ways.  The biggest way is poor performance.

Deja Dup is meant to get a "full" backup every month, not "until it gets full".  That's just asking for backups that cannot be restored.
If you want/need more control over the backups, there are other tools like duplicity or rdiff-backup.  Deja Dup is based on duplicity, so it has the same failings.  rdiff-backup is more like rsync and don't do encryption, but it does have methods to more easily control the amount of storage used in a consistent way.  rdiff-backup has to be run as root to do system backups.

---

### Post by JamButty on 2018-10-26
Needing to mount that partition and delete old files manually, by whatever method, is not ideal, but not a real problem. I have needed to wipe and reload several times in the last couple of years and the restore via Deja dup has been easy and reliable. Not being able to backup at all, that's a problem. Deleted everything under trash by terminal. No change.
```
cd /media/homer/Backups
homer@homer-Inspiron-3847:/media/homer/Backups$ ls
lost+found
homer@homer-Inspiron-3847:/media/homer/Backups$ cd .Trash-1000
homer@homer-Inspiron-3847:/media/homer/Backups/.Trash-1000$ ls
files  info
homer@homer-Inspiron-3847:/media/homer/Backups/.Trash-1000$ rm -rfi files
rm: descend into directory 'files'? y
rm: remove regular file 'files/text.txt'? y
rm: remove directory 'files'? y
homer@homer-Inspiron-3847:/media/homer/Backups/.Trash-1000$ rm -rfi info
rm: descend into directory 'info'? y
rm: remove regular file 'info/text.txt.trashinfo'? y
rm: remove directory 'info'? y
homer@homer-Inspiron-3847:/media/homer/Backups/.Trash-1000$ ls


```

---

### Post by JamButty on 2018-10-26
Even formatted that partition. Same deja dup error. Will try de/re-install of deja dup
---nope. Same old same old.

---

### Post by TheFu on 2018-10-26
Did see some other threads saying that session data was stored somewhere in ~/.cache/ for dejadup. Perhaps that got corrupted somehow?  Also, they said that deja dup works differently based on the userid running it.  root does different things than normal users and has separate session cache data. 

I don't remember which directory specifically keeps the session data, so be certain to find the correct one for each user account.

There was an old bug that sounds similar [https://answers.launchpad.net/deja-dup/+question/129952](https://answers.launchpad.net/deja-dup/+question/129952)
And some around similar errors you've mentioned: [https://bugs.launchpad.net/deja-dup?field.searchtext=space&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.omit_dupes=on](https://bugs.launchpad.net/deja-dup?field.searchtext=space&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.omit_dupes=on)

[https://bugs.launchpad.net/deja-dup/+bug/913949](https://bugs.launchpad.net/deja-dup/+bug/913949) blames using GVFS for not telling the truth about available storage. The suggested fix is to mount using the mount command (or autofs).  I don't know if this will actually work, but perhaps it will?

That's all the ideas I have. Sorry.

---

### Post by JamButty on 2018-10-26
there was a deja dup folder under .cache. I deleted that prior to reinstall. There must be other traces elsewhere though, as the reinstalled deja-dup had all my old preferences (what to backup, what to ignore, where to backup) pre-populated.
I am the only user and root so no complications there. I did not find rdiff-backup in the main repository. Looked at "back in time", which advertises as a gui for rsync, but it documentation left me thinking it less reliable than deja dup HAD been.

---

### Post by TheFu on 2018-10-26
I've used back-in-time. It uses rsync + hardlinking to do versioning.  The downside to rsync-based backup tools is that the changes in permissions and ownership are lost as they change over time.  Also, they must have a Unix file system that supports POSIX permissions, hardlinks, ACLs, etc.  That means NTFS and and the FAT-based file systems cannot be used.  All the backups look like rsync mirrors. They are organized into date directories.  Fairly self explanatory.  The "smart-versioning" stuff in BiT is sorta slick. They make "snapshots" (as they call them, but they aren't real LVM/ZFS snapshots) every hour or two, then selectively delete those over time. It is smart.

rdiff-backup should be in the ubuntu repos.  I've been using it for 8+ yrs and can't remember ever adding a PPA. It works similar to rsync, but only the most recent backup looks like a mirror. Older versions are stored as compressed, reverse-diffs. Metadata about the permissions, owners, groups, ACLs are maintained too. To restore form the last backup, just copy the file or rsync it back. Simple.  In general, my backups take 2-7 minutes with rdiff-backup. I keep 60-120 days of versioned backups, depending on the risk factors for the system. It is in one of the repos that is built-into Ubuntu. Perhaps you need to enable the multiverse?

If you are happy with Deja Dup, I'd stay with that or a variant that is based on Duplicity. Duplicati is another alternative with a GUI.  I tested it on Windows long ago. It didn't fit my performance requirements and I didn't like that the backup files weren't easily accessed without using the tool.

Did you try using a real mount instead of gvfs?  Did that not work?

If it doesn't and you've reviewed the links I posted tonight, perhaps the best answer is to wait for others to chime in. Someone with DejaDup experience should be able to help more than me.

---

### Post by JamButty on 2018-10-27
heavy sigh. Sorry for wasting your time, my mistake. I had thought from seeing earlier full backups, that there was substantial compression in the backup files. I knew I had 5GB more in source files than free space on target, but assumed compression was way more than enough to compensate for that. Apparently there is no compression at all. Once I limited the source files, backup went normally.
Thanks for all your input TheFu.
over and out.

---

### Post by TheFu on 2018-10-27
So, what showed the correct sizes?   Was GVFS lying?

I thought duplicity did do compression.  All the other tools do as well.  Heck, my rdiff-backup for my desktop has lots of versions, but only uses 1.2x the source storage size.  My main desktop is 17G in size, but 60 days of versioned backups (I backup everything needed to restore the system to the same config and data, not the OS)....
I generate a summary report every Sunday morning, so from last Sunday ... ```

        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Sun Oct 21 01:15:06 2018         6.59 GB           6.59 GB   (current mirror)
Sat Oct 20 01:15:06 2018         14.5 MB           6.60 GB
Fri Oct 19 01:15:06 2018         7.14 MB           6.61 GB
...
Fri Aug 24 01:15:05 2018         5.51 MB           7.47 GB
Thu Aug 23 01:15:07 2018         17.1 MB           7.49 GB
```
That is 1.14x the original.  1.2x is conservative estimate, but YMMV.  I keep media on other systems, clearly.

---

### Post by JamButty on 2018-10-27
It was not that any system was giving me wrong sizes, though there is a small variance between the default "Files" gui, which I guess GVFS stands for and the "Disks" partitioning data app. I had in my head firmly and apparently very wrongly, that DejaDup backup files took up about 25% less space than their source files. The backup I was trying was actually less than 1GB larger than the free space on the backup partition, but that was enough to tank the backup.  I omitted one huge directory, bringing the source files down to 68GB and the backup files were also 68GB. I will be doubling the size that partition soon.

---

