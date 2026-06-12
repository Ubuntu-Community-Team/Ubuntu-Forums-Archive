---
title: "Moved /home to separate partition; cannot login; /etc/fstab file shows &quot;0&quot; data;"
date: 2013-03-29
forum: General Help
---

### Post by jimbrook on 2013-03-29
12.04 LTS Gnome

I successfully moved my /home and all its contents to a separate partition following the official Ubuntu guide "https://help.ubuntu.com/community/Partitioning/Home/Moving"  I cannot log in under my usename and password.  Each time I try it sends me back to the login page.  I can log in as Guest.

Using a rescue disk, I attempted to edit my /etc/fstab file.  The file shows no data.  I do have a backup of the original /etc/fstab as per the guide.  Gedit will not let me replace the edited fstab file.  

Logging into a terminal as root will not allow me to start-up and programs in the broken system.  Each drive is reported as read only access.

Need Help.  I can't afford to do a clean install without trying every possible solution.  -- jim

---

### Post by steeldriver on 2013-03-29
When using rescue disk are you sure you are attempting to edit the correct fstab file i.e. the one on your actual system - not the running rescue system?

How are you logging in as root? if you are booting into the recovery console (via the grub menu) then it's normal for the filesystem to be mounted read-only. You can change that either by exiting back to the menu and selecting the 'filesystem check' or 'with networking' options, or by issuing a remount command ('mount -o remount,rw /')

HOWEVER if you can log in OK as guest maybe it is just your X session that has got messed up so BEFORE resorting to any of those let's see if you can log in to your normal user account through one of the virtual terminals by hitting Ctrl-Alt-F1 (or Ctrl-Alt-F2 etc. ... Ctrl-Alt-F7 will take you back to the GUI).

---

### Post by r.stiltskin on 2013-03-29
I suspect that you may have skipped a step in the moving guide, maybe the one that changes the mount point of the new home partition to /home:
```

# (identifier)  (location, eg sda5)   (format, eg ext3 or ext4)      (some settings) 
UUID=????????   /home    ext3          nodev,nosuid       0       2
```

By *rescue disk*, did you mean an actual "System Rescue CD" or something else?

When you tried to edit fstab, you were in all likelihood attempting to edit files on the rescue disk.  Instead, you have to mount the partition of your hard disk containing your root file system and edit /etc/fstab there.  If you're using System Rescue CD, after it boots up, run startx, then run gparted (*be careful, don't make any changes to your disks, we're only using gparted to get some information*) and look at the disk info it displays to find the correct location of your root file system, e.g., /dev/sda2, or whatever...

While you're at it, see if you can identify your new home partition in the gparted display, right-click on it, click "information" and make note of its UUID (to be sure that you enter it correctly in fstab).

Then close gparted, create a mount point in the rescue file system, e.g.:
```
mkdir /mnt/temp
```
Then mount your root filesystem there.  In the following command, replace the * with the appropriate partition number you determined in gparted.
```
mount /dev/sda* /mnt/temp
```

Now you can edit or replace your old fstab file, which will be located at /mnt/temp/etc/fstab.

After rebooting, you should be OK, assuming you used the correct UUID for the new home partition.

---

### Post by jimbrook on 2013-04-01
Thanks for replies.  I ended up fouling up the new /home partition [ext4].  The partition showed no type and no dated in gparted.  So, figuring everything was lost, I formatted back to ext4.  Now, I show a lost+found folder that is locked. The file is 31 GB, about the size of the home folder I was moving to the new /home.  Any suggestion on getting the files back? Also, I need to successfully set up /home on the separate partition, going forward.

---

### Post by carl4926 on 2013-04-01
> [COLOR=#000000]I show a lost+found folder that is locked. The file is 31 GB[/COLOR]But how big is the partition for /home ?

---

### Post by jimbrook on 2013-04-02
600 GB.  My intention was to use that partition as /home for multiple distributions and to eventually back-up a Win drive.  I use Linux 90% of the time but have to revert down to winxp from time to time

---

### Post by r.stiltskin on 2013-04-02
Be careful with that.  Why do you want backups of your Windows files to be accessible (and therefore vulnerable) in your Linux /home directory?  Wouldn't it be safer to create a completely separate partition for that?

Also, your /home directory contains configuration files for various packages which are frequently different in different distributions.  That can cause conflicts if you're planning to have multiple distros installed at the same time, and confusion when you have to figure out which config belongs to which distro.  So if they'll all be in the same partition, you might want to at least use a different username in each distro.

I do like to have a separate /home partition because it's convenient to be able to reinstall Linux or do a distribution upgrade without losing personal data files, etc.  But if you want to share data between different distros it might be a good idea to put that data in a separate directory (outside of the users' home directories) and create links to it from each of the homes.  And if you want to also be able to access the shared data from Windows, you might want to put it in a separate NTFS partition, mount that shared-data partition in all of your Linux distros and link to it from all of their /home directories.  (I don't suggest mounting your primary Windows partition in Linux, to protect it from accidental damage.)

Just my opinion.

---

### Post by r.stiltskin on 2013-04-02
Back to your question:  the lost+found directory is created to provide a place for fsck to save lost file fragments that it finds during startup after the system shuts down abnormally.  I've never heard of any formatting tool saving data in lost+found.  That wouldn't really make sense: if you decided to reformat a full directory, you would end up with a newly-formatted, but already full, directory.

How did you determine that the lost+found is 31 GB?  Actually that sounds like the default 5% of total partition space that most linux filesystems reserve for root use.  What output do you get if you run
```
du -h --max-depth=1 /home
```

What happened to your original /home directory -- the one on your original disk that you renamed to old-home or whatever?  There are some utilities that can recover deleted files if they haven't been overwritten with new data.  One that I've heard of is called foremost although I've never had to use it.

Another one is called photorec which despite its name apparently also works on other types of files.  It doesn't seem to be in the Ubuntu repository, but it is free so you can download & install it directly from [cgsecurity.org]("http://www.cgsecurity.org/wiki/PhotoRec").

You may be able to recover data from the original disk, or from the new disc even though you have reformatted it (if you actually did successfully copy anything to the new one, which seems questionable).

Either way, you'll have to decide whether the deleted data is worth the effort, since at the very least you'll have to examine each and every recovered file to see if it's complete, and I guess rename each one.  The degree of success will depend on the extent to which that disk space has been overwritten, and on the amount of fragmentation of the files.  It's important to avoid doing any writing to that disk until your recovery efforts are complete.

---

### Post by oldfred on 2013-04-02
Photorec is in the repository, it is part of testdisk. So just install testdisk and you also get photorec. 

I have used Photorec a couple of times. It is slow as it scans entire drive by byte, finds only the file by extension, so no filenames and finds multiple copies of a file if you saved it more than once. But it works.
And it can then take a long time to determine which file is really which file. Photos and a few files have internal data that make it easy to rename.

I also agree with r.stiltskin, do not share /home if installing different distributions. The advantage of separate /home is for new installs. But if sharing data then separate data partitions work better. I have two data partitions, one NTFS from when I still booted XP, and one Linux formatted for all new data. I should merge my NTFS data back into my Linux data, but then have to totally reorganize, so have not done that yet.

 [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

   Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

---

### Post by jimbrook on 2013-04-03
Thanks to "Stiltskin"  and "Oldfred".  I may just give up the ghost on this one and start over.   I can boot into Ubuntu as a new user but my original user name just returns me back to the login.  I set my "new user" as admin.  My original is set up as admin. Should I (can I) delete my original username and start-over by creating an recreating my original user name in the separate home partition?  Is there a command line or series of commands that would perform that task efficiently?  Again, thanks for the help and suggestions. The biggest reason I don't want to just reload the distro from scratch is a lot of software downloaded from repository and other sources plus Dropbox, the Chrome world, etc.

---

### Post by steeldriver on 2013-04-03
it may still be just an ownership / permissions problem

> **steeldriver said:**
> if you can log in OK as guest maybe it is just your X session that has got messed up so BEFORE resorting to any of those **let's see if you can log in to your normal user account through one of the virtual terminals by hitting Ctrl-Alt-F1** (or Ctrl-Alt-F2 etc. ... Ctrl-Alt-F7 will take you back to the GUI).

---

### Post by r.stiltskin on 2013-04-03
I'm assuming that you're logged in as newuser and that newuser is a member of the sudo group.

First be sure that newuser is a member of all of olduser's groups, except the initial one (the one named "olduser").  You can check each user's group memberships by running
```
groups olduser newuser
```
Now suppose for example that the output of that is
olduser : olduser adm cdrom sudo dip plugdev lpadmin sambashare
newuser : newuser adm cdrom sudo
To make newuser a member of the additional groups you would run
```
usermod -G adm,cdrom,sudo,dip,plugdev,lpadmin,sambashare newuser
```
listing ALL of olduser's groups (except "olduser"), including all the groups that newuser is already in, separated by commas (no blank spaces between groups).  Be sure you use an uppercase 'G'.

Then you can remove olduser by
```
sudo userdel -r olduser
```

If you want to create a new "olduser" you can
```

sudo useradd -m -G adm,cdrom,sudo,dip,plugdev,lpadmin,sambashare newuser -s /bin/bash olduser
```Important: lowercase 'm', uppercase 'G', lowercase 's'.
Then don't forget to set olduser's password:
```

sudo passwd olduser
```

---

