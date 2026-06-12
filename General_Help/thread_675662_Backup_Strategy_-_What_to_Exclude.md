---
title: "Backup Strategy - What to Exclude"
date: 2008-01-22
forum: General Help
---

### Post by simpsonsfan74 on 2008-01-22
Recently I have been working on creating a backup solution for my laptop.  I use dar (Disk ARchive, [http://dar.linux.free.fr/](http://dar.linux.free.fr/)), available in the Ubuntu repositories to create my backup.  I did some research to find out what system directories to exclude, but everyone seemed to have a different opinion.  (Should I exclude /dev or not?)  I thought I'd share with everyone what I came up with so y'all don't have to do the same research.  Below is a list of directories I excluded from my system backup with an explanation by each.

**[SIZE="2"]Exclusions[/SIZE]**
**/dev** - Feisty and Gutsy (Edgy?) use udev to create the /dev tree on system boot.  Since this tree is not persistent when the system is off, I excluded it.  It should be noted that my Gutsy installation had a /dev directory with static device nodes (moved to /dev/.static/dev upon system boot).  Since I could not figure out a way to save the /dev/.static/dev directory as /dev in dar, I make a quick backup and removed it with seemingly no consequences.  (If you save /dev/.static/dev in dar and then later restore it, udev remounts the directory to /dev/.static/dev/.static/dev, which gets a little confusing...)

**/tmp** - I excluded this because it should not be used as persistent storage by any program.  It also included a few files specific to the X.org session currently running that I didn't want to included in my backup.

**/lost+found** - This directory is used by the system to place orphaned files.  I have never seen anything in it, but I excluded it in favor of using the *mklost+found* command after the backup is restored.

**/proc** - The Proc subsystem is mounted here and should not be backed up.

**/sys** - The SysFS subsystem is mounted here and should not be backed up.

**/lib/modules/`uname -r`/volatile** - The first round of backups I made did not exclude this directory, and upon restoring the backup, got some crazy messages about bad modules.  It turns out this directory is mounted as tmpfs, so it gets recreated on system boot.

**/mnt** - I did not want my system backup to include any outside filesystems mounted here.  You may, however, feel differently.

**/media** - Same as /mnt.  I have my shared partition mounted here and felt it necessary to exclude it from the backup.

**backup files** - If you are using dar like I am, and your backup is being created in a subdirectory of the tree you are backing up, make sure to exclude your backup from an infinite loop.

**[SIZE="2"]Directories NOT excluded from backup[/SIZE]**
**/var/run** - This directory is mounted as tmpfs, so you might want to exclude it from your backup.  I found, however, that this directory still contained files even when the system wasn't running.  Since it did not affect the system to include it in the backup, I just left it there.

**/var/lock** - This directory was empty on my system, so I just left it in the backup.  It should be noted, however, that like /var/run, it is mounted as tmpfs.

**[SIZE="2"]Conclusions[/SIZE]**
As you may realize by now, I have just discussed everything currently mounted by the system.  If you don't mind excluding /var/run and /var/lock, you can use the -M (--no-mount-points) option provided by dar to exclude all running mount points.  This will exclude everything covered here on a Gutsy installation.

---

