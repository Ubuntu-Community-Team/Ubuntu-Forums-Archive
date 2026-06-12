---
title: "Backing up an entire HD"
date: 2018-08-04
forum: General Help
---

### Post by COKEDUDE on 2018-08-04
Are there any recommended methods for Backing up an entire HD? I want to backup my data. I do not care about the OS file. I just want my work, movies, and music. I have about 600 GB of work, movies, and music so a bit worried about fragmentation if I just copy and paste.

---

### Post by The Cog on 2018-08-04
So you have another drive ready to copy them to? In that case, I would use rsync. I have occasionally seen problems using copy/paste in a file manager with huge direstory trees. rsync is trustworthy.

---

### Post by HermanAB on 2018-08-05
Set up an rsync backup script in /etc/cron.daily or cron.weekly.  The trick is to tell rsync to backup everything and only exclude a few things.  That way, you never need to change the script again.

---

### Post by COKEDUDE on 2018-08-22
Are there any recommended options to use with rsync? Is there a verbose option and progress option? How long does copying this much data usually take? Like 2 hours, 5 hours?

---

### Post by NM5TF on 2018-08-22
> **COKEDUDE said:**
> Are there any recommended options to use with rsync? Is there a verbose option and progress option? How long does copying this much data usually take? Like 2 hours, 5 hours?

you might find some answers here  [https://www.comentum.com/rsync.html]("https://www.comentum.com/rsync.html")

or possibly here    [https://unix.stackexchange.com/questions/373018/using-rsync-for-backing-up-my-stuff-on-an-external-hdd]("https://unix.stackexchange.com/questions/373018/using-rsync-for-backing-up-my-stuff-on-an-external-hdd")

I also found this that might help.....

```
Full system backup

This section is about using rsync to transfer a copy of the entire / tree, excluding a few selected folders. This approach is considered to be better than disk cloning with dd since it allows for a different size, partition table and filesystem to be used, and better than copying with cp -a as well, because it allows greater control over file permissions, attributes, Access Control Lists and extended attributes.

rsync will work even while the system is running, but files changed during the transfer may or may not be transferred, which can cause undefined behavior of some programs using the transferred files.

This approach works well for migrating an existing installation to a new hard drive or SSD.

Run the following command as root to make sure that rsync can access all system files and preserve the ownership:

# rsync -aAXv --exclude={"/dev/*","/proc/*","/sys/*","/tmp/*","/run/*","/mnt/*","/media/*","/lost+found"} / /path/to/backup/folder

By using the -aAX set of options, the files are transferred in archive mode which ensures that symbolic links, devices, permissions, ownerships, modification times, ACLs, and extended attributes are preserved, assuming that the target file system supports the feature.

The --exclude option causes files that match the given patterns to be excluded. The contents of /dev, /proc, /sys, /tmp, and /run are excluded in the above command, because they are populated at boot, although the folders themselves are not created. /lost+found is filesystem-specific. The command above depends on brace expansion available in both the bash and zsh shells. When using a different shell, --exclude patterns should be repeated manually. Quoting the exclude patterns will avoid expansion by the shell, which is necessary, for example, when backing up over SSH. Ending the excluded paths with * ensures that the directories themselves are created if they do not already exist.
Note:

    If you plan on backing up your system somewhere other than /mnt or /media, do not forget to add it to the list of exclude patterns to avoid an infinite loop.
    If there are any bind mounts in the system, they should be excluded as well so that the bind mounted contents is copied only once.
    If you use a swap file, make sure to exclude it as well.
    Consider if you want to backup the /home/ folder. If it contains your data it might be considerably larger than the system. Otherwise consider excluding unimportant subdirectories such as /home/*/.thumbnails/*, /home/*/.cache/mozilla/*, /home/*/.cache/chromium/*, and /home/*/.local/share/Trash/*, depending on software installed on the system. If GVFS is installed, /home/*/.gvfs must be excluded to prevent rsync errors.

You may want to include additional rsync options, such as the following. See rsync(1) for the full list.

    If you use many hard links, consider adding the -H option, which is turned off by default due to its memory expense; however, it should be no problem on most modern machines. Many hard links reside under the /usr/ directory.
    You may want to add rsync's --delete option if you are running this multiple times to the same backup folder. In this case make sure that the source path does not end with /*, or this option will only have effect on the files inside the subdirectories of the source directory, but it will have no effect on the files residing directly inside the source directory.
    If you use any sparse files, such as virtual disks, Docker images and similar, you should add the -S option.
    The --numeric-ids option will disable mapping of user and group names; instead, numeric group and user IDs will be transfered. This is useful when backing up over SSH or when using a live system to backup different system disk.
    Choosing --info=progress2 option instead of -v will show the overall progress info and transfer speed instead of the list of files being transferred.


```

good luck...

tommy

---

