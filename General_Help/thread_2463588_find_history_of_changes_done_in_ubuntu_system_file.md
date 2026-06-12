---
title: "find history of changes done in ubuntu system files"
date: 2021-06-14
forum: General Help
---

### Post by tojonukokhadush on 2021-06-14
i have a question out of my curiosity. i am wondering if there's any mechanism by which we can find the history of changes made in any files especially system files in linux and therefore in ubuntu! or can such thing be expected even? thanks in advance.

---

### Post by deadflowr on 2021-06-14
Out of the box you'd probably have to rely on reading through various log files which may or may not be useful.
With lots of cruft to siphon through unrelated to what you want to know.

But there are tools like tripwire or AIDE that you can install which would make it far easier to deal with.
In general they're intrusion detection/file integrity checking tools, but they run by doing a base system scan of the file system.
This creates a database and then subsequent scans reveal any changes to the files in the system since the last scan was done.

---

### Post by scorp123 on 2021-06-15
> **tojonukokhadush said:**
> i am wondering if there's any mechanism by which we can find the history of changes made in any files especially system files in linux and therefore in ubuntu!

Depends on how the system was setup. E.g. Ubuntu with **ZFS** as filesystem offers that functionality out of the box, as everytime you install something a snapshot will be taken. And you can browse those snapshots and compare the files inside of them.

Example from one of my systems:

On a ZFS setup the "**/boot**" filesystem resides on a ZFS pool called "**bpool**". So to the see all snapshots that exist of "**bpool**" I'd type a command such as:

```

> zfs list -t snapshot -o creation,space -s creation -r bpool
CREATION               NAME                                                      AVAIL   USED  USEDSNAP  USEDDS  USEDREFRESERV  USEDCHILD
Tue Mar  2  7:18 2021  bpool/BOOT/ubuntu_r07xkn@FreshInstall_WorkingOK_20210301      -    56K         -       -              -          -
Tue Mar  2  7:32 2021  bpool/BOOT/ubuntu_r07xkn@DataPool_Imported-OK                 -     8K         -       -              -          -
Tue Mar  2 12:34 2021  bpool/BOOT/ubuntu_r07xkn@Everything_WorkingOK_20210302        -     8K         -       -              -          -
Sun Apr 18  3:15 2021  bpool/BOOT/ubuntu_r07xkn@Backup_2021-04-18                    -   157M         -       -              -          -
Sun May  9 19:17 2021  bpool/BOOT/ubuntu_r07xkn@Backup_2021-05-09                    -    72K         -       -              -          -
Tue May 11  1:07 2021  bpool/BOOT/ubuntu_r07xkn@autozsys_837u48                      -    72K         -       -              -          -
Tue May 11  1:41 2021  bpool/BOOT/ubuntu_r07xkn@autozsys_hhs6ex                      -    88K         -       -              -          -
Wed May 12 16:10 2021  bpool/BOOT/ubuntu_r07xkn@autozsys_hyzi9v                      -    56K         -       -              -          -
Wed May 12 21:54 2021  bpool/BOOT/ubuntu_r07xkn@autozsys_1ihpf0                      -    48K         -       -              -          -
Sat May 15  2:38 2021  bpool/BOOT/ubuntu_r07xkn@autozsys_0hpp1d                      -    48K         -       -              -          -
Mon May 17 13:59 2021  bpool/BOOT/ubuntu_r07xkn@autozsys_mnvd5c                      -    56K         -       -              -          -
Tue May 18 22:27 2021  bpool/BOOT/ubuntu_r07xkn@autozsys_yp1t6t                      -    64K         -       -              -          -
Wed May 19  9:32 2021  bpool/BOOT/ubuntu_r07xkn@autozsys_s79yfb                      -    64K         -       -              -          -
Thu May 20  9:23 2021  bpool/BOOT/ubuntu_r07xkn@autozsys_7hvkjk                      -    64K         -       -              -          -
Tue May 25 10:57 2021  bpool/BOOT/ubuntu_r07xkn@autozsys_j76hpe                      -    56K         -       -              -          -
Wed May 26 10:07 2021  bpool/BOOT/ubuntu_r07xkn@autozsys_nwf9vi                      -     0B         -       -              -          -
Thu May 27 10:20 2021  bpool/BOOT/ubuntu_r07xkn@autozsys_jgruvm                      -     0B         -       -              -          -
Thu May 27 22:22 2021  bpool/BOOT/ubuntu_r07xkn@autozsys_d8gs1w                      -     0B         -       -              -          -
Wed Jun  2 14:06 2021  bpool/BOOT/ubuntu_r07xkn@autozsys_ynckg2                      -     0B         -       -              -          -
Thu Jun  3 10:08 2021  bpool/BOOT/ubuntu_r07xkn@autozsys_p7qqg8                      -    72K         -       -              -          -
Thu Jun  3 10:25 2021  bpool/BOOT/ubuntu_r07xkn@autozsys_dyd4m5                      -    88K         -       -              -          -
Fri Jun  4 11:09 2021  bpool/BOOT/ubuntu_r07xkn@autozsys_7tfnz4                      -    56K         -       -              -          -
Tue Jun  8  2:49 2021  bpool/BOOT/ubuntu_r07xkn@autozsys_mgbmzr                      -    56K         -       -              -          -
Wed Jun  9 11:04 2021  bpool/BOOT/ubuntu_r07xkn@autozsys_c1fzhx                      -    64K         -       -              -          -
Thu Jun 10  6:51 2021  bpool/BOOT/ubuntu_r07xkn@autozsys_conc7f                      -     0B         -       -              -          -

```

I did a manual snapshot on March 2 that I called "FreshInstall_WorkingOK_20210301" ... I can enter into it and take a look what's inside:

```
# cd /boot/.zfs/snapshot/FreshInstall_WorkingOK_20210301/
# ls -al

total 184993
drwxr-xr-x 4 root root       19 Mar  2 01:44 .
drwxrwxrwx 2 root root        2 Jun 10 10:35 ..
-rw-r--r-- 1 root root   237718 Apr 20  2020 config-5.4.0-26-generic
-rw-r--r-- 1 root root   237730 Jan 27 22:44 config-5.4.0-66-generic
drwxr-xr-x 2 root root        2 Mar  2 01:10 efi
drwxr-xr-x 2 root root        2 Mar  2 01:10 grub
lrwxrwxrwx 1 root root       27 Mar  2 01:21 initrd.img -> initrd.img-5.4.0-66-generic
-rw-r--r-- 1 root root 82430171 Mar  2 01:41 initrd.img-5.4.0-26-generic
-rw-r--r-- 1 root root 82531431 Mar  2 01:44 initrd.img-5.4.0-66-generic
lrwxrwxrwx 1 root root       27 Mar  2 01:10 initrd.img.old -> initrd.img-5.4.0-26-generic
-rw-r--r-- 1 root root   182704 Aug 18  2020 memtest86+.bin
-rw-r--r-- 1 root root   184380 Aug 18  2020 memtest86+.elf
-rw-r--r-- 1 root root   184884 Aug 18  2020 memtest86+_multiboot.bin
-rw------- 1 root root  4736015 Apr 20  2020 System.map-5.4.0-26-generic
-rw------- 1 root root  4746873 Jan 27 22:44 System.map-5.4.0-66-generic
lrwxrwxrwx 1 root root       24 Mar  2 01:21 vmlinuz -> vmlinuz-5.4.0-66-generic
-rw-r--r-- 1 root root 11657976 Apr 23  2020 vmlinuz-5.4.0-26-generic
-rw------- 1 root root 11690752 Jan 27 23:14 vmlinuz-5.4.0-66-generic
lrwxrwxrwx 1 root root       24 Mar  2 01:21 vmlinuz.old -> vmlinuz-5.4.0-26-generic

```

What I get here is the content of my "/boot" filesystem how it was back on March 2, 2021 when this system was freshly installed.

And I can of course compare that against my current contents of "/boot" that are live now:

```

root: /boot/.zfs/snapshot/FreshInstall_WorkingOK_20210301 # ls -al /boot/

total 189569
drwxr-xr-x  4 root root       19 Jun  9 11:06 .
drwxr-xr-x 20 root root       26 Mar  2 07:30 ..
-rw-r--r--  1 root root   237851 Apr 14 18:35 config-5.4.0-73-generic
-rw-r--r--  1 root root   237851 May  8 02:45 config-5.4.0-74-generic
drwxr-xr-x  4 root root     4096 Jan  1  1970 efi
drwxr-xr-x  4 root root     4096 Jun 10 06:51 grub
lrwxrwxrwx  1 root root       27 Jun  3 10:09 initrd.img -> initrd.img-5.4.0-74-generic
-rw-r--r--  1 root root 84686305 Jun  9 11:06 initrd.img-5.4.0-73-generic
-rw-r--r--  1 root root 84694981 Jun  9 11:06 initrd.img-5.4.0-74-generic
lrwxrwxrwx  1 root root       27 Jun  3 10:09 initrd.img.old -> initrd.img-5.4.0-73-generic
-rw-r--r--  1 root root   182704 Aug 18  2020 memtest86+.bin
-rw-r--r--  1 root root   184380 Aug 18  2020 memtest86+.elf
-rw-r--r--  1 root root   184884 Aug 18  2020 memtest86+_multiboot.bin
-rw-------  1 root root  4750832 Apr 14 18:35 System.map-5.4.0-73-generic
-rw-------  1 root root  4751152 May  8 02:45 System.map-5.4.0-74-generic
lrwxrwxrwx  1 root root       24 Jun  3 10:09 vmlinuz -> vmlinuz-5.4.0-74-generic
-rw-------  1 root root 11764480 Apr 14 18:37 vmlinuz-5.4.0-73-generic
-rw-------  1 root root 11763968 May  8 03:42 vmlinuz-5.4.0-74-generic
lrwxrwxrwx  1 root root       24 Jun  3 10:09 vmlinuz.old -> vmlinuz-5.4.0-73-generic

```

It's already easy to tell that there were several Linux kernel upgrades between March 2 and now, e.g. the March 2 snapshot still lists files belonging to kernel 5.4.0-26 whereas the current content of "/boot" lists kernel 5.4.0-74.

I could now use every Linux tool in the arsenal (e.g. tools such as "**diff**" and so on) to see what exactly has changed between each file in the snapshot and the currently live one, e.g. the GRUB config.

There are other mechanisms, tools and ideas (e.g. regularly uploading your config files to a Git repository and then checking the differences via the "git" tool ...) but if you are new simply installing your Ubuntu system with ZFS might probably be the easiest approach as it doesn't require much else other than making sure that "Use ZFS" is selected during the installation.

Please be aware that ZFS will swallow the whole disk, it doesn't do well with other OS'es. If you intend to share the same SSD / the same harddrive with a different OS then ZFS is a no-go (that other OS would get destroyed during installation).

---

### Post by Impavidus on 2021-06-15
If you keep versioned backups of your system files, you can see the history of changes there too. But most people never make versioned backups of system files, as most people keep them at the defaults. There's no need for a backup if you can restore by reinstall.

---

### Post by TheFu on 2021-06-15
> **tojonukokhadush said:**
> i have a question out of my curiosity. i am wondering if there's any mechanism by which we can find the history of changes made in any files especially system files in linux and therefore in ubuntu! or can such thing be expected even? thanks in advance.

Versioned backups would know this at the level each different version is created.  I keep between 60 and 180 days of versioned backups for most systems. That doesn't include the OS binaries, but it does include all settings and config files at the personal and system level. I also capture a list of installed packages, nightly, just prior to making the backups, so recreating the system is fairly easy. Most backup tools that can do versioning will make it easy to see differences between non-binary files too. 
The really great thing about versioned backups is that when files are removed, that still gets recorded.

Some changes over time:
```
$ locate target  | grep /Backups/hadar/rdiff-backup-data/increments/etc/systemd/system | egrep -v 'dir$'
...
/Backups/hadar/rdiff-backup-data/increments/etc/systemd/system/multi-user.target.wants/snap-snapd-11402.mount.2021-03-23T01:35:06-04:00.missing
/Backups/hadar/rdiff-backup-data/increments/etc/systemd/system/multi-user.target.wants/snap-snapd-11402.mount.2021-05-12T01:35:04-04:00.snapshot
/Backups/hadar/rdiff-backup-data/increments/etc/systemd/system/multi-user.target.wants/snap-snapd-11588.mount.2021-04-05T01:35:34-04:00.missing
/Backups/hadar/rdiff-backup-data/increments/etc/systemd/system/multi-user.target.wants/snap-snapd-11588.mount.2021-06-01T01:35:04-04:00.snapshot
/Backups/hadar/rdiff-backup-data/increments/etc/systemd/system/multi-user.target.wants/snap-snapd-11841.mount.2021-05-12T01:35:04-04:00.missing
/Backups/hadar/rdiff-backup-data/increments/etc/systemd/system/multi-user.target.wants/snap-snapd-12057.mount.2021-06-01T01:35:04-04:00.missing
/Backups/hadar/rdiff-backup-data/increments/etc/systemd/system/multi-user.target.wants/snap.anbox.container-manager.service.2021-05-09T01:35:04-04:00.missing
...

```

While we can use snapshots, their lifespan is usually much less. I keep a snapshot around only for a week or so. For my use, snapshots are for clean backup needs and for trying new software that might be dangerous. 
Perhaps ZFS snapshots are more efficient and only roll off the disk when storage is tight and it is necessary?

Anyways, lots of ways to solve this. Just need to think the Unix-way a little.

---

### Post by tojonukokhadush on 2021-06-16
its way more complicated than i expected; whole new information to me. thanks a lot. would do some basic research.

---

### Post by TheFu on 2021-06-16
> **tojonukokhadush said:**
> its way more complicated than i expected; whole new information to me. thanks a lot. would do some basic research.

Until about 1995, Unix systems were managed by professional administrators. Only then did typical power-users start with Linux and around 2005, typical end-users. The expectation that a professional administrator was involved stuck, especially for questions that most end-users don't ask.

Versioned backups have been around 40+ yrs and solve all sorts of questions, problems, issues.

We all need backups, so it is assumed in the Unix world that every system will have those, at least.  Which means, problems which are easily answered by having versioned backups don't need any other solution, so why bother making one? It would be wasted effort for little return.

But if all you want to know is whether files have been changed, a 'find' command can be run daily or weekly to capture that information.

```
sudo find / -type f -mtime -1 -print | tee /tmp/changed-files-$(date "+%F")
```
Run that daily (no more) and you'll have a list of all the files that changed.  Add more options if you want more information from 'find' ; try the -ls option, to get lots of details, 1 line per file.  Use **explainshell.com**  to learn the different options of find OR check out the find manpage.  Find is one of those commands with nearly infinite capabilities that isn't intuitively obvious how to use, but there are **Top 10** and **Top 50 examples of Find** webpages.  I found seeing 10+ examples of find use extremely useful.

Just be prepared that there will be thousands of files on an active desktop:
```
$ wc -l /tmp/changed-files-2021-06-16
7360 /tmp/changed-files-2021-06-16
```
7300 lines means 7300 changed files in the last day.  That surprised me.  Most where in the browser cache directories.  Remove those and the list becomes much more manageable.
```
$ egrep -v .cache  /tmp/changed-files-2021-06-16 | wc -l
166
```

166 lines changed.  Looking through those and many are still browser-tracking related.  Remove them ... 
```
$ egrep -v mozilla  /tmp/changed-files-2021-06-16 | wc -l
30
```

Hummm. Now we are getting somewhere.  Nothing unexpected in that list.  Password DB, alarm-clock settings, some batch queue files, and a few scripts that I updated yesterday which are still fresh in my memory.  Nothing in /etc/, which is where system settings belong.

See how learning to use a few 40+ yr old Unix tools can answer questions easily?  If I'd like to see the list daily, then those commands could be dropped into a text file, add a 1 line script header, then called from cron - the task scheduler daily.

I think I'll update my "Learning Linux Thought Shift Needed" blog article [https://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed](https://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed) with this information as another example.

Unix is different from Windows. We don't need a GUI tool to find many answers to our questions.  Those answers just take a little knowledge and 10 minutes of thought to think of a way the existing files on the system could be used.  But with most things, we don't know what we don't know.  

Excellent question. Good way to show off a few of the built-in text processing tools on Unix systems and how those can be put together to create answers to real-world questions.

---

### Post by dragonfly41 on 2021-06-16
Just an idea below .. untested ..

In my Ubuntu 20.04 there is a utility **lynis** which can audit systems through cronjob. 
Lynis is in Ubuntu repo.

Then on reading the tips posted above, I found this article ..

[https://linux-audit.com/find-differences-between-two-daily-lynis-audits/](https://linux-audit.com/find-differences-between-two-daily-lynis-audits/)

I wonder if this might be relevant for you?

---

