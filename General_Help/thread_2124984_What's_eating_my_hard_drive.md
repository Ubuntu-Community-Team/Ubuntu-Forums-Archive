---
title: "What's eating my hard drive?"
date: 2013-03-12
forum: General Help
---

### Post by Troilus on 2013-03-12
A few weeks ago, the partition containing my / drive was full such that when I try to log into Gnome I get the error message "The configuration defaults for GNOME Power Manager have not been installed correctly.", and I cannot log into a graphical session (though I can use terminal).  A search on the forums showed that this error occured because there was insufficient disk space.

So I cleaned out my / partition. I emptied the apt cache, I got rid of software I wasn't using. And I was left with an install of about 3.5Gb on the / partition (/dev/sdb4 on my system).  Then, using a live CD and gparted, I increased the size of my / partition to 19 Gb just to make sure it was future proof.  And when I rebooted, all was well. 

But this evening, the problem is back.  All 19Gb appears to have been used up.  But when I reboot with the live CD and run Disk Usage Analyzer on /dev/sdb4 it shows that the partition contains only 3.5Gb of files - there should be 15.5Gb of empty space.  There is nothing extraneous in the drive's /var or /tmp folders.   So I cannot, after hours of looking, work out what is taking up all the space.

I have searched the forums but haven't found a similar problem.  Any suggestions on what to look for to resolve the issue?  For now, I've resized the partition again to buy some time.

Thanks

System details:
Ubuntu 10.04 (lucid)
Kernel 2.6.32-45
Four partitions on drive: Windows, Home, Root, Swap

---

### Post by Bashing-om on 2013-03-12
Troilusl Hi !

In the situation as you describe it. I would look at run-a-muck log files. Identify what error is filling up the logs and correct that issue.
Here is a handy terminal code to see system file usage; Terminal code:
```
du -h --max-depth=1 | sort -hr
```This command list from the "current working directory" down into the file hierarchy. Thus one "Changes Directory" to look at the various top directory contents: "/" is the top directory of the entire file system;
```
 cd / # Changes Directory to "root"
ls -l # list all sub-directories
# make a note of all directories to be inspected (/var in this instance)
cd /var
du -h --max-depth=1 | sort -hr
cd /home
du -h --max-depth=1 | sort -hr
cd /var/log

```
In the event that it is /var/log/ that is huge, the "log file viewer is handy to read the log files (dash -> log file viewer) in order to determine where the fault might lie.

That should be a good start ->[INDENT=5]hope this helps


[/INDENT]

---

### Post by Troilus on 2013-03-13
Ozarks

Thank you for the reply. Using du -h --max-depth=1 I discovered that the used space was in a folder /media/Backup.

Then I realised that my own stupidity was the problem.  I had set an automatic backup to run: it was supposed to go to a mounted external hard-drive (at /media/Backup).  But the drive wasn't plugged in.  So it seems that once a month the backup has been running, and, not finding the mounted drive, it has been creating the folder /media/Backup.

Backups have now been moved to where they ought to be, and 16Gb has been freed up.

This is solved, but unfortunately, I'm going to have to open another thread because, in my haste to clear space on my root, I seem to have deleted something that is used in the boot!

---

### Post by CharlesA on 2013-03-13
If you have a script that is supposed to be running your backups, you can run a check to make sure the drive is mounted before running the backup commands.

Check out [mountpoint]("http://linux.die.net/man/1/mountpoint").

---

### Post by Bashing-om on 2013-03-13
Troilus; Pleased you are making progress// Do make a new post for the new problem and mark this thread as solved: work-a-round:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.
Problem still ? -> graphical instruction:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Don't overlook CharlesA's advisement ![INDENT=2]see ya there

[/INDENT]

---

