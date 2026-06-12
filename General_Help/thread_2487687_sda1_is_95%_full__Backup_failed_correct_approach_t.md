---
title: "sda1 is 95% full / Backup failed: correct approach to removing unnecessary files?"
date: 2023-06-12
forum: General Help
---

### Post by ozark_hillbilly on 2023-06-12
Hello,

When I used the BACKUP utility to save my /HOME user area onto a separate hard drive subfolder the backup failed when it informed me 
sda1 was less than 1 GB. I am perplexed why the sda1 [filesystem root] partition is filling up when the folder it was intstructed to use is on another physical drive.
 
I checked the /var subdirectory and there are no huge files there.

Why does the BACKUP utility even access filesystem root when doing its /HOME backup operation?

I have attached a screenshot of "DISKS" showing sda1 is 95% full.

What is the correct approach to freeing up space? 

thank you....

---

### Post by QIII on 2023-06-12
Have you tried looking at /var/**log ** and cleaning up old logs?

Maybe do

```
sudo journalctl --vacuum-time=3d

```

You can lower 3 to 1 (or even a fraction) for days to get rid of more.

---

### Post by ActionParsnip on 2023-06-12
What is the output of
```

df -h

```

---

### Post by yancek on 2023-06-13
I can't read the text clearly in your image but it appears your first partition is the / filesystem and partition 3 is a separate /home partition.  Is that correct?  What was the output of the df -h command on the / and /home partitions before running Disks?  Compare that to the current output of df -h.  If the / file system was not 95% full before the backup, it would appear it was copied to the wrong device/partition.  If the / partition was that full before using Disks, your best bet is as suggested, to check /var/logs and/or use the find command to find the largest files which you may delete.

---

### Post by TheFu on 2023-06-13
If you want to backup your HOME and only your HOME, then use a command like this:
```
sudo  /usr/bin/rdiff-backup  \
        --exclude-sockets --exclude-device-files --exclude-fifos \
        --include /home \
        --exclude '**'   /       /Backups/
```

Ref: [Https://ubuntuforums.org/showthread.php?t=2482517&p=14125329#post14125329](Https://ubuntuforums.org/showthread.php?t=2482517&p=14125329#post14125329)

You can run that same command over and over to get different versions.  Only changed data will be transferred. It is very efficient both in time and space used.
To prevent it from filling up the backup storage, you'll want to trim the oldest backup sets off.  I typically keep 90-180 days of backup sets, so to remove any that are older than that, use
```
sudo  /usr/bin/rdiff-backup  --remove-older-than "90D"  --force /Backups
```

The most recent backup appears as a mirror, so restoring files is just a copy from the backup area. If you need older versions of a file, directory, everything, then rdiff-backup has a *--restore-as-of*  option that takes times, dates, versions ... it is very flexible.

The only caveat is that the target storage, /Backups, in my example, needs to be a Unix file system. Not NTFS. Not exFAT. Not FAT32.  Ext4 or f2fs are good choices.

That's really all you need.  Put those 2 commands into a {file}, chmod +x {file} - now it is a "script".  Mount the backup storage to /Backups and run the script. Run it daily or weekly, then sleep better knowing you have backups for everything in any HOME directories on the system.  This will get all the data for all the userids on the system, not just 1.  Remember, Linux is always a multi-user OS.  

This really isn't enough for a "system" backup, but for many people, it is more than sufficient.  For system backups, I have a little longer script and more directories in the "--include" list.

Of course, you'll need to ensure the space for the source files/directories will fit into the target storage. 
```
sudo du -sh /home  # Check the source
sudo du -sh /Backups  # Check the target
```

For 90 days of versioned backups, you'll want the target area to be 30% larger than the source files. Of course, YMMV.

---

### Post by ozark_hillbilly on 2023-06-13
QIII,

Holy crap! That journalctl command freed up about 2.2G and gave me some breathing room!!! Thanks.
I now need to continue looking for other superfluous files to remove. I wish there was a batch/script file
a user could run that would go in and do a super, but safe, vacuum of filesystem root.

---

### Post by ozark_hillbilly on 2023-06-13
df -h output:

ed@ed-G41MT-S2PT:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           792M  1.7M  790M   1% /run
/dev/sda1        23G   20G  2.4G  90% /
tmpfs           3.9G   57M  3.9G   2% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/loop0      128K  128K     0 100% /snap/bare/5
/dev/loop1       56M   56M     0 100% /snap/core18/2751
/dev/loop2       56M   56M     0 100% /snap/core18/2745
/dev/loop4       64M   64M     0 100% /snap/core20/1891
/dev/loop3       64M   64M     0 100% /snap/core20/1879
/dev/loop5       74M   74M     0 100% /snap/core22/634
/dev/loop6      219M  219M     0 100% /snap/gnome-3-34-1804/90
/dev/loop7      219M  219M     0 100% /snap/gnome-3-34-1804/93
/dev/loop8      350M  350M     0 100% /snap/gnome-3-38-2004/137
/dev/loop9      350M  350M     0 100% /snap/gnome-3-38-2004/140
/dev/loop10     461M  461M     0 100% /snap/gnome-42-2204/102
/dev/loop11      66M   66M     0 100% /snap/gtk-common-themes/1515
/dev/loop12      92M   92M     0 100% /snap/gtk-common-themes/1535
/dev/loop14      13M   13M     0 100% /snap/snap-store/959
/dev/loop13      46M   46M     0 100% /snap/snap-store/638
/dev/loop15      54M   54M     0 100% /snap/snapd/19122
/dev/loop16      54M   54M     0 100% /snap/snapd/19361
/dev/sda3        78G   21G   53G  29% /home
tmpfs           792M   96K  792M   1% /run/user/1000
/dev/loop17      74M   74M     0 100% /snap/core22/750
/dev/loop18     461M  461M     0 100% /snap/gnome-42-2204/105
/dev/sdb1        71G   41G   27G  61% /media/ed/04e8bdce-0446-4973-96c5-7cd2afd52d5d1
ed@ed-G41MT-S2PT:~$

---

### Post by ozark_hillbilly on 2023-06-13
"....your first partition is the / filesystem and partition 3 is a separate /home partition. Is that correct? "

Yes, that is correct. I am fairly confident I used the right pointer reference to locate the backup on the other hard drive.
I will definitely use your "find" suggestion to keep looking for extraneous files.

Which areas of filesystem root should not be tampered with and which areas are ok to remove? I would think /logs files under
/var is a fair target. I definitely do not want to get overzealous and remove anything that will screw the OS/kernal up.

Thanks for your input.

edit - The GNU findutils is an amzing tool! Looking at the documentation now.

---

### Post by ozark_hillbilly on 2023-06-13
TheFu,

Man, that was a killer post you gave me!! I need to digest all that info and try to setup my backups in the manner
you suggested. I will visit the link provided and give it a go. 
I think I am in good shape because almost all my drive partitions are configured as Ext4.

Thanks alot!!!!!

edit -

"Mount the backup storage to /Backups and run the script."

I created /Backups directory. Is this the correct syntax for linking my other drive partition [sdb1] to /Backups?

sudo mount -t Ext4 umask=0222  /dev/sdb1  /Backups

thanks...

---

### Post by deadflowr on 2023-06-13
You could probably clear up some more space by removing snaps completely.
Since you don't have any worthwhile to have snapd installed.
The only snap you have listed is snap-store.
The rest are all underlying support snaps.
You could simply uninstall all of them and remove any snapd apt packages (if installed) and it should clear up some space at least.

snap store can be replaced with gnome-software (and/or synaptic if you never want to install snaps or flatpak packages.)
(synaptic only deals with apt packages, gnome-software has extra plugins that allow installing apt, snap and flatpak packages)

---

### Post by ozark_hillbilly on 2023-06-13
Is this link a good roadmap to removing snap? :

[https://itsfoss.com/remove-snap/#remove-snap-entirely-from-ubuntu-use-with-extreme-caution-]("https://itsfoss.com/remove-snap/#remove-snap-entirely-from-ubuntu-use-with-extreme-caution-")

ed@ed-G41MT-S2PT:~$ snap list
Name               Version           Rev    Tracking         Publisher   Notes
bare               1.0               5      latest/stable    canonical&#10003;  base
core18             20230503          2751   latest/stable    canonical&#10003;  base
core20             20230503          1891   latest/stable    canonical&#10003;  base
core22             20230531          750    latest/stable    canonical&#10003;  base
gnome-3-34-1804    0+git.3556cb3     93     latest/stable/&#8230;  canonical&#10003;  -
gnome-3-38-2004    0+git.6f39565     140    latest/stable    canonical&#10003;  -
gnome-42-2204      0+git.587e965     105    latest/stable    canonical&#10003;  -
gtk-common-themes  0.1-81-g442e511   1535   latest/stable/&#8230;  canonical&#10003;  -
snap-store         41.3-71-g709398e  959    latest/stable/&#8230;  canonical&#10003;  -
snapd              2.59.4            19361  latest/stable    canonical&#10003;  snapd
ed@ed-G41MT-S2PT:~$

---

### Post by ozark_hillbilly on 2023-06-14
Bump...

---

### Post by dragonfly41 on 2023-06-15
You might find this Stacer GUI tool helps you drivng over the bumps in the road ..

[https://oguzhaninan.github.io/Stacer-Web/](https://oguzhaninan.github.io/Stacer-Web/)

eg go to Uninstaller > Snap Packages

and other dashboards for maintenance.

---

### Post by TheFu on 2023-06-15
> **ozark_hillbilly said:**
>  
"Mount the backup storage to /Backups and run the script."

I created /Backups directory. Is this the correct syntax for linking my other drive partition [sdb1] to /Backups?

sudo mount -t Ext4 umask=0222  /dev/sdb1  /Backups

thanks...

does that mount command work?  Why set the umask for ext4? I wouldn't. Use permissions to handle that.  There are example options (probably) in /etc/fstab for mounting ext4 file systems.
Not leaving backup storage connected all the time is smart, but if you have to manually do anything with backups, then human laziness will cause the process to fail.  I know it did for me in the early 2000s.  All I had to do was run 1 script, once a week ... and still I failed to do it.  This is why backup need to be 100% automatic. We humans are lazy. ;)  Know it.  Love it. Live it.

I just put this backup how-to up: [https://lpi.jdpfu.com/2023-Backups/2023-Backup-How-To.html](https://lpi.jdpfu.com/2023-Backups/2023-Backup-How-To.html) ... hopefully, it is clear and fills in some blanks.

---

### Post by ozark_hillbilly on 2023-06-15
Thank you for that link. :!:

---

### Post by ozark_hillbilly on 2023-06-15
I go thte umask bit out of a Ubuntu Linux book and did not realize it was unnecessary for Ext4. The pitfalls of being a neopyhte.
I appreciate your latest link as it may fill in some areas I am unsure about. Thanks again.

---

### Post by TheFu on 2023-06-16
> **ozark_hillbilly said:**
> I go thte umask bit out of a Ubuntu Linux book and did not realize it was unnecessary for Ext4. The pitfalls of being a neopyhte.
I appreciate your latest link as it may fill in some areas I am unsure about. Thanks again.

Either the book is mistaken, or the type of file system it was mounting was non-native Linux, like NTFS?
[https://www.linuxcommand.org/tlcl.php](https://www.linuxcommand.org/tlcl.php) is the book I've used to teach beginning Linux at the local University.  Start from the beginning and do 1 chapter a week, complete all the exercises for the chapter --- including the "extra" ones.  In 12 weeks, you'll have a better grasp AND you will have learned things in the right order.

Unix/Linux knowledge builds on prior skills.  Really can't jump from baby stuff to 10 yr old stuff - there's just so much early development knowledge that is required.  The learning curve is very steep, if you don't have a good introduction.  The first 12 chapters ARE that intro.

---

### Post by ozark_hillbilly on 2023-07-16
snapd is deleted now....=d>

---

### Post by ozark_hillbilly on 2023-07-16
thank you!!!!!!
I have tro do that book for sure.....

---

### Post by gezzer2 on 2023-07-17
@TheFu .. thank you for the CLI book ive just started going through it. nothing like a refresher course ...

---

### Post by TheFu on 2023-07-17
No book is as complete as the local manpages, but most people just need to know a few commands and a few options for those commands.  The more you use them, the most non-obvious connections between the different commands will be made.  After a year or two, if you keep using the CLI, something will probably "click" in your brain and a whole new level of connections between the commands will be clearer.  You'll see patterns in options between similar tools.  You'll be better at guessing the option that makes output cleaner, easier to read, more useful.  You'll also note when certain options don't behave as expected and those exceptions will stick in your brain.

Hopefully, you'll start seeing how connections between different computers are really, really, easy, thanks to ssh and ssh-based tools.  You'll understand why the default prompt in the shell is brilliant - seems it is exactly the format needed for some commands to xfer files.  It is perfect for scp, sftp, rsync, for example.  Very, very, handy.

And if you haven't learned tab-completion - STOP WHAT YOU ARE DOING NOW!  _**Go learn tab-completion.**_  It is something that makes working in a shell/CLI environment so much more efficient and effectively prevents ever mistyping a directory for filename wrong.  Without tab-completion, the shell interface sucks.  With it, it can be a joy to use and extremely efficient.

---

