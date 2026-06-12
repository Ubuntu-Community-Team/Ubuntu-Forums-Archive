---
title: "Can I backup/restore my OS at the *file level* ?"
date: 2016-11-28
forum: General Help
---

### Post by mikey93898 on 2016-11-28
Hello friends,

I still don't understand something about the fundamental nature of linux, and I'm hoping you can help. 

Can I do a "full system backup", not with a drive image (dd), but at the file level? I feel like this is possible, but I haven't been able to find any place that identifies it as standard practice, or even 100% confirms it. Usually I back up an OS with the "dd" command, and end up with a nice little (huge) IMG file, which compresses well if I've written zeros to the empty space prior. Restoring is typically a reliable process.

But what about backing up like this:
[LIST=1]
[*]Boot to LIVE USB thumb
[*]Use rsync to create a mirror of all files under root dir "/" on my main partition (assuming I only have sda1=boot, sda2=OS)
[*]Zip and be done
[/LIST]

And then perhaps to restore:
[LIST=1]
[*]Reinstall OS from scratch, apparently just to get a boot partition that works again
[*]Shutdown, reboot into LIVE USB thumb
[*]Use rsync to restore files to root dir "/"
[*]Shutdown
[*]Reboot to OS normally
[*]???
[*]Profit ?
[/LIST]

If this is something that could work, what are the caveats? Would I need to make sure the new kernel matches the old backup kernel or something? I feel like doing this in windows would bring ruin and dishonor to my family ... but with linux it seems somewhat ... logical?

I ask now because I'd rather know beforehand whether this is going to bork my system or not down the road, lol. Thank you for your time :)

~Mike

---

### Post by sudodus on 2016-11-28
Yes it is possible :-) You can use ***rsync*** or ***tar*** for this purpose.

**1. Root partition**

a. All the content of an Ubuntu installed system in UEFI mode is stored as files.

b. Almost the content of an Ubuntu installed system in BIOS mode is stored as files. In this case you need to install grub separately which is fairly easy to do.

**2. Swap partition**

You need to take care of the swap partition separately (in both cases). This can be avoided if you use a swap file.

-o-

I made the ***One Button installer*** to make it easy to install a linux system in an old computer without enough RAM for the standard installer. There is a tool to create a tarball too, that you can use to do what you want to do, ***to create a backup***, which will be stored in a compressed tarfile, a 'tarball'.

The One Button Installer works in BIOS mode, and is not necessary in UEFI mode, where you can simply make a tarball (with sudo to be able to manage all files and all permissions). Avoid mounting any partitions in the system, that you want to back up.

See this link

[https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

If you want to use this method, I suggest that you ***compress with gzip***, which does not compress as 'tight' but is much faster than xz.

---

### Post by mastablasta on 2016-11-28
with rdiff-backup you should be able to do this automatically. 

not sure if you really need the whole system backed up like that though. user and confirg files should be enough. maybe list of installed apps.

--

@sudodus - why would you need to backup swap?

---

### Post by sudodus on 2016-11-28
You are right mastablasta,

1. rdiff-backup is a good alternative :-)

2. and you need not back up swap, but the original poster probably wants a swap partition in the new drive and it should match the 'swap line' in /etc/fstab.

If they want to use rsync or tar, swap is one of the things to fix separately in order to get a working system again, while a tool might fix it automatically (for example the One Button Installer).

---

### Post by kpatz on 2016-11-28
You can do backups at the file level.  One way is just to back up important files, such as those in /home, /etc and the output of dpkg --get-selections to get a list of installed packages.  Then to restore, you reinstall from scratch, reinstall packages and restore your files.

Another option is to copy everything from the root down with rsync, then you can restore everything almost as easily.  To restore, you'd just boot off a live CD or USB, set up your partitions and file systems, mount them, rsync everything back, chroot to the mounted root, install grub and update /etc/fstab as needed, reboot and go.  Also with a file level backup, it's easy to restore individual files or directories as needed.

---

### Post by mikey93898 on 2016-11-28
Awesome! I went ahead and tried this technique out on a Raspberry Pi last night and it was a success. I had an img file from **dd **and used that. Basically my process was the same:

1. Install plain vanilla minimal "raspbian" linux distro, just so the thing would boot
2. Pull the SD card out of the Raspberry Pi, insert into computer, wait for desktop to automount it to /media/mike/blablabla
3. Mount my *.img* file to a local folder
4. Make a Desktop folder called "joy"
5. Make two symlinks inside ~/Desktop/joy  ... "sd-card" pointing to mounted sd card, "img" pointing to the mounted image file
6. rsync with --archive and -X and -A, for all the fun archive flags, extra attributes, and acl's
7. Unmount everything and put the card back in my Raspberry Pi ... suddenly it worked

The thing worked on the first try!! I have yet to verify all the symlinks worked correctly. I'll have to hunt for them later.

My guess is my main gotcha would be ... if I had any hardlinks? I don't have a clue how those would survive this type of backup/restore.

As for the usefulness of this process. I already do a full file-based backup with rsync from all my desktop stations to backup drives. Basically just /home .... but now that I know this works, I'll probably add one extra job called "OS Backup" or something, and backup everything except /home. This way I can backup the systems after making tedious install configs, but not have to run them very often. Maybe once per blue moon.

So excited. Please throw out other gotchas if you can think of them.

Oh and awesome OBI app... very cool too.

---

### Post by sudodus on 2016-11-29
Congratulations :KS

You can use the option -H to copy hard links with rsync. I often use this command line starting with a 'dry run'

```
sudo rsync -Havn source/ target
```

and when I see that it wants to do what I intended, I remove the option -n to do it,

```
sudo rsync -Hav source/ target
```

It can be tricky with symlinks. I think it is best to copy them as they are, let them remain syslinks, not to follow them. Finally, it helps to use sudo, otherwise there might be problems with ownership and permissions.

-o-

When you feel that the problem/question in the first post is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED. We can still continue to exchange ideas in this thread.

If you have other problems/questions, it is better to create a new thread with a good descriptive title.

---

### Post by HermanAB on 2016-11-29
Well... the traditional way to backup a system is with the Tape Archiver tar.  The more efficient way is with rsync.

Basically, just save all directories, except the transient things like proc, sys, dev, tmp, mnt, swap, which don't have anything useful in them.

However, the above is easier said than done, since if you make a backup of a file that is in use, then the copy may be corrupted, since the buffers in RAM may not have been flushed to disk.  Therefore it is best to boot off a USB memory stick, then mount the target directories in /mnt one by one and then tar them.

Also, consider that there is actually no point in making a copy of the whole system, since Linux is available for free download from hundreds of mirrors the world over already.  Therefore, the usual advice is to forget about backing up everything and just save your data.  If you have a special system with lots of configuration tweaks, make a tar ball of /etc and save that.

---

### Post by mikey93898 on 2016-11-29
Thanks, Sudodus! I'll play with that hardlink option and see what happens. I checked my symlinks and they all appear to be fine ... maybe it was because rsync was not following them by default. I got lucky I guess.

Herman - I partially agree with you, but am still not 100% sure that all config files happen inside /etc. Qemu comes to mind, that saves VM disks to /var/libvirt/.... or somesuch by default. So maybe I would save etc and var also?

If I used tar instead of rsync, or used tar after rsync, are there any extra gotchas, like destruction of extra attributes / ACLs / Symlinks / Hardlinks / etc?

Marked thread as solved, woot!

---

### Post by sudodus on 2016-11-29
Thanks for sharing your results :-)

***tar*** works for me, when run with sudo. But when I want incremental backup, and when I want to files easily available, I use ***rsync***.

---

### Post by SeijiSensei on 2016-11-29
> **mikey93898 said:**
> Thanks, Sudodus! I'll play with that hardlink option and see what happens. I checked my symlinks and they all appear to be fine ... maybe it was because rsync was not following them by default. I got lucky I guess.
No, you're not lucky.  Both Linux and rsync are well-designed.  Rsync copies symlinks as links by default.  Ubuntu and most other Linux distributions use relative symlinks so they are preserved in backups. 

I can't think of the last time I hard linked anything.

---

### Post by mikey93898 on 2016-11-30
> **SeijiSensei said:**
> No, you're not lucky.  Both Linux and rsync are well-designed.  Rsync copies symlinks as links by default.  Ubuntu and most other Linux distributions use relative symlinks so they are preserved in backups. 

I can't think of the last time I hard linked anything.

Would it be safe to assume no major linux distributions use hard links for OS install?

---

### Post by 1clue on 2016-11-30
> **kpatz said:**
> You can do backups at the file level.  One way is just to back up important files, such as those in /home, /etc and the output of dpkg --get-selections to get a list of installed packages.  Then to restore, you reinstall from scratch, reinstall packages and restore your files.

I strongly advise against a file-level backup of system binaries.  It's ***incredibly**** better* to use dpkg --get-selections instead, as @kpatz said above.

That said IMO rsync is not a valid backup tool.  It may work fine as part of a backup plan, such as to stage files on a specific server which will then be backed up.

One of the big reasons to have a backup is to recover accidentally deleted or corrupted files.  Rsync will happily delete or corrupt the destination directory without any qualms.

Backups should be a collection of all relevant data as of a certain date/time. While it's possible to have a bootable backup that's a whole lot of extra trouble for not much saved time. It's much more effective in my opinion to backup system configs, user files, your data (e.g. /var/lib/mysql, or rather a directory containing a sql dump of /var/lib/mysql) and the package list.

---

### Post by SeijiSensei on 2016-11-30
> **mikey93898 said:**
> Would it be safe to assume no major linux distributions use hard links for OS install?

I'm in no position to make such blanket statements, but I've not seen any in my years of using CentOS or Ubuntu.

As for backup strategies, the script I run creates a separate directory each day and uses rsync to populate it.  I rotate out the oldest directory every five to eight days depending on the amount of space available on the backup device.  Of course, none of this is equivalent to writing backup tapes and storing them off-site in case of a fire.  I also dump my PostgreSQL and MySQL databases on the server to text each night before the backup runs.

---

### Post by 1clue on 2016-11-30
@SeijiSensei,

Is rsync faster than a plain recursive copy? It seems that what you're doing isn't too different from what I do at the first stage, I just use a 'sudo cp -rax ...' and write it to my backup device folder. If you rsync to a new folder each time it will copy everything.

I copy things (like you're saying) to a staging directory which is always online and always contains my data as of the most recent backup. For example, **sudo cp -rax /etc /var/backups/$HOST/etc** and a few more lines to get /home and such.  Then I copy that to a dated folder (/mnt/backup/2017-11-30/<hostname>/path/to/mount) in a slot-loaded SATA drive. Then I pop the backup device out and take it off-site to put in a safe.

As far as backup strategies go, if the backup isn't disconnected and moved off site and kept off-line then it's not really a backup because it's not proof against theft, fire, lightning strike, or ransomware.

If the backup doesn't make a fresh (non-replacing) copy of your data at a given point in time, then you lose the ability to restore some file which was deleted before your most recent backup.

If it can't get you back to a working state easily and reliably, it's not really a backup because retrieving data after a mishap is the entire point of a backup.

---

### Post by SeijiSensei on 2016-11-30
My main servers are all virtual hosts at Linode.  I pay to have nightly and weekly snapshots taken.  If something goes seriously wrong, I can spin up a new host and recreate the server from the most recent backup.  If the problem is less severe, I have my off-site rsync archive.

I don't know whether rsync is any faster than cp when copying entire directories without updates.  Certainly rsync is very fast when it can use its diff method to send only file changes, but that doesn't apply in my case.  I like it because it's a simple and reliable program with a lot of options.  I use "--files-from" and "--exclude-from" pretty often to separate the backup script itself from the lists of files to include and exclude.

---

### Post by kingneutron on 2016-11-30
> I strongly advise against a file-level backup of system binaries.  It's ***incredibly**** better* to use dpkg --get-selections instead, as @kpatz said above.

--That is one method, but I strongly disagree with you on that being a time-efficient method of doing a full bare-metal system restore.  For one thing, it involves using Internet bandwidth (which can be slow) to download/upgrade installed packages - which delays getting the system back online quickly.

--Disk space is CHEAP these days. You can get a 2TB USB3 drive for under $80 (or a 2TB SATA NAS drive for under $90) and use that just for backups.  If you're a desktop user with a customized system and you want to get back online *exactly* as you were in a minimum amount of time, you shouldn't cut corners. (And definitely keep a burned copy of System Rescue CD around.)

--Attached are some scripts you can use to completely bare-metal recover a Linux system (standard install to ext4; no btrfs, LVM or RAID; no separate /boot partition.)  I'm a little paranoid (having lost data in the past), so I do file-level AND image-level backups of the OS.  **My case scenario is backing up the entire system before doing an apt-get upgrade, in case something breaks.**  I have also used the fsarchiver method to clone Ubuntu installs to another PC.  

> Can I do a "full system backup", not with a drive image (dd), but at the  file level? I feel like this is possible, but I haven't been able to  find any place that identifies it as standard practice, or even 100%  confirms it. Usually I back up an OS with the "dd" command, and end up  with a nice little (huge) IMG file, which compresses well if I've  written zeros to the empty space prior. Restoring is typically a  reliable process.

--**For the original poster**: fsarchiver is pretty close  to what you're already doing with 'dd' - but it has multi-cpu compression, flexibility, and  you don't have to zero the free space first. If restoring to the same hardware, it also restores the filesystem UUID so you don't have to modify grub or fstab.

```

(from ' man fsarchiver ')
DESCRIPTION
       fsarchiver  is a system tool that allows you to save the contents of a filesystem to a compressed archive file. The file-system can be 
restored on a partition which has a different size and it can be restored on a different file-system. Unlike tar/dar, FSArchiver also creates 
the filesystem when it  extracts  the  data  to  partitions.
       Everything is checksummed in the archive in order to protect the data. If the archive is corrupt, you just lose the current file, not
 the whole archive.

```

**NOTE** Required packages for these scripts: 
fsarchiver
pv
lzop
gzip
tar

--Also note these aren't intended to be general-use scripts, you should edit them according to your needs before running them.  (I am trying to convey a method here, not a drop-in solution. Feel free to ask questions.)

--How I run them (as root)

bkpcrit # quick backup of really critical files
bkphome # since I have a separate /home partition
bkpsys # tar method, supports file-level restores
bkpsys-2fsarchive # for full bare-metal restore of the root partition

' apt-get update;apt-get upgrade '

---

