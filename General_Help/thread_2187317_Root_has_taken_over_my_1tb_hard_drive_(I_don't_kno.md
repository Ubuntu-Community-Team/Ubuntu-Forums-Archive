---
title: "Root has taken over my 1tb hard drive (I don't know how else to explain it, honestly)"
date: 2013-11-11
forum: General Help
---

### Post by wiccanarchy on 2013-11-11
okay so, I just installed Ubuntu on a fresh 160gb hard drive, it installed fine without problems, but here's my situatuation, and it's a weird one.
So, basically, in my computer, there are 3 hard drives, one 500gb with windows 7 and some programs on it, one 160gb with Ubuntu on it, and, a 1tb hardrice, which used to have many games, mp3s and photographs on it, which has been somehow wiped during the process of installing Ubuntu, and been replaced by a copy of Ubuntu. 

This wouldn't matter all too much if I could actually do anything with that drive, I literally can't format it, delete any files from it, install anything to it, or even copy files from it. It doesn't show up on windows 7 anymore either in the "My Computer" section. I also noticed that when i checked the properties of the drive it was owned by "root", which, to my understanding, is the equivalent of the Admin user account on Windows.

SO basically, what I want to do is format this drive and get an explanation to how this actually happened.
Thanks in advance, a newbie.

---

### Post by SuperFreak on 2013-11-11
You should be able to format the drive by using a Live USB or Ubuntu disk and going into GParted. Just be careful that you format the correct drive/partitions

---

### Post by wiccanarchy on 2013-11-11
Sorry, don't quite know what you mean by that, very new to Ubuntu.

---

### Post by wiccanarchy on 2013-11-11
Bumping because this is annoying as hell and I can't really do much with my computer at the minute.

---

### Post by oldfred on 2013-11-11
If partition is NTFS, it will be always owned by root. If you cannot see it from Windows that is a separate issue and it may need chkdsk or other repairs. Usually the Linux NTFS driver will not even mount a NTFS partition that needs chkdsk or is hibernated to prevent damage that chkdsk may not fix.

       Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

Better mount paramters using this template.
      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

   For ext4:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2

   ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

   ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a

---

### Post by Johan De Cauwer on 2013-11-11
Ok. look at this in order to understand gparted:
[http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-using-gparted-to-partition-a-hard-disk/](http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-using-gparted-to-partition-a-hard-disk/)
Now, I don't know what version of Ubuntu you installed but basically this lets you 'format' anything, beware!
I guess you can boot into Ubuntu as well as in Windows. Perhaps the 1T drive is still available from that side and the data are not lost. On the other hand, if you have a backup...

---

### Post by wiccanarchy on 2013-11-11
I have 13.10, and nope, even Gparted won't let me format the drive, the option is kinda greyed out. 
And the file system for that drive is ext4.

---

### Post by wiccanarchy on 2013-11-11
QUick question, what would unmounting the drive via Gparted do?

---

### Post by Johan De Cauwer on 2013-11-11
> **wiccanarchy said:**
> 
And the file system for that drive is ext4.
That's bad, because that means the drive is formatted with loss of data but most probably usable from the Ubuntu side. Perhaps - probably - it is mounted or in use and that's the reason why you can't change anything with Gparted. The earlier answer asked to boot from usb or Live CD for that reason. So you can either do that or boot into windows and reformat from there...

---

### Post by oldfred on 2013-11-11
If ext4 I might run fsck on it to see if it just has some minor issues.

If a separate drive you do not have to use live installer. But do have to make sure unmount, which sound like tha tis all it is.

 #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by SuperFreak on 2013-11-11
You are correecd the drive has to be unmounted before formatting. However you need to do this from a live DVD disk or USB of Ubuntu. Did you install from a DVD disk or USB? If so boot to that disc and then use GParted.

---

### Post by The Cog on 2013-11-11
It seems there's some guessing going on here. Can you run these commands and post the output: that should help us understand what we're dealing with:
```
sudo parted -l
df -h
mount
```And if you could point out which drive is the problem one that might help too.

---

