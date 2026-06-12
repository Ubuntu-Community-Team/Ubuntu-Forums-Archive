---
title: "tar option --listed-incremental causes segmentation fault"
date: 2016-10-31
forum: General Help
---

### Post by Randy_Bass on 2016-10-31
I'm getting a segmentation fault when I use tar with the option“--listed-incremental” in a Bash script. I can use tar without this option and it works fine. I can do updates with the --update operation rather than --create, and that works fine as well, appending new files to the end of the tar. The “--listed-incremental”option requires a separate file to store the tar file metadata (filename.snar), and then creates a separate tar file of just the differences each time it's run. So I run this one time, and it creates the tar and snar file just fine. I run it a second time, changing the tar filename, with the same snar file, and I get a segmentation fault. I have six different filesystems I'm trying to back up, some are standard partitions and some are LVM logical volumes, all ext4 filesystems, and I get the segmentation fault on each one. However, I'm also doing a backup of a subdirectory rather than a complete filesystem, and that works fine without the segmentation fault. Here's an echo of the command to expand all the variables, followed by the output of the tar command, follow by a third line where I output the error code from the tar command:

    ```
tar --create --one-file-system --no-check-device --auto-compress --warning=no-file-ignored --file=/home/randy/Backup/home4/pictures/update-week-40-to-43/Pictures-week-40-to-43.1.tar/home/randy/Pictures --listed-incremental=/home/randy/Backup/home4/pictures/update-week-40-to-43/Pictures-week-40-to-43.snar
/home/randy/Backup/bkup-scripts2/source/bkupf-tar-backup.sh: line361: 8831 Segmentation fault   (core dumped) tar "${archive_opts_a[@]}" "${file_opt}" "${source_directory}" "${exclude_opt}" "${increment_opt}" &>> "${gc_logfile}"
>>>ERROR in creating tar update.  Error value: 139

```

I have run this on both Ubuntu 14.04 32 bit and Xubuntu 16.04 32 bit (kernel 4.4.0-43)with the same results.

I found this post on the subject where the person was able to solve the problem by copying tar from  a different location. 

[https://ubuntuforums.org/showthread.php?t=2295549&highlight=tar+segmentation+fault](https://ubuntuforums.org/showthread.php?t=2295549&highlight=tar+segmentation+fault)

Well, I guess that was a defective installation of tar. I've tried clean/check/autoremove/update/upgrade, but got the same results afterwards. Also, these filesystems are on two drives, one an SSD and one a HDD. It only happens with the option “--listed-incremental”. I take that out and it doesn't happen. So I really don't think I have a problem with both of my drives going bad at the same time.

I also found this link from 2010 that mentions a bug and a patch.

[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=575298](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=575298)

Supposedly, this bug was fixed with Tar 1.25.1. I'm currently using tar version 1.28-2.1,so has the bug somehow reappeared? Am I missing something in my command line that is causing this?

---

### Post by TheFu on 2016-11-01
Can't help with the tar issue. Haven't used that method for backups since 1995.  For anything over a few hundred MBs, there are other solutions which work very well.  Any interest in those options?

Sometimes old-school stuff is really great, but sometimes it is old and not used much because better (for certain values of "better") solutions to the problem have arrived.

---

