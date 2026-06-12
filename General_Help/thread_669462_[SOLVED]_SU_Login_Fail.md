---
title: "[SOLVED] SU Login Fail"
date: 2008-01-16
forum: General Help
---

### Post by Rwild on 2008-01-16
Okay... I have a few issues with my new install that I did not have while running the live disk.  I will address one at a time... Hopefully all in this one thread.

I am attempting to log in as su in a Terminal window.  I enter my password and it tells me login failed.  Isn't my SU password the same as the login password when Ubuntu starts?:confused:

---

### Post by p_quarles on 2008-01-16
The root account has a locked password in Ubuntu. To get a root shell, use:
```
sudo -i
```
which will indeed take your password.

For the record, though, there's nothing you can't do using sudo + command.

---

### Post by Rwild on 2008-01-16
Ah, OK.  I guess that works then... ;)

I am having an issue with my drives.  I have 2 HDDs on one ribon and 2 optical drives on another.  I am only picking up one of each in "Computer". Any way to fix this a I could view everything without issue on the live disk?

---

### Post by p_quarles on 2008-01-16
You probably don't need to boot the live disk at all. Can you post the results of the following two commands?:
```
cat /etc/fstab
```
and
```
sudo fdisk -l
```

---

### Post by Rwild on 2008-01-16
> root@rwild-desktop:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=7f8a30af-e3f4-4422-bab8-64a405f05de7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=b0200b0c-759c-43cc-bfba-92e666590ae7 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0



> root@rwild-desktop:~# sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfdb3796f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1       60801   488384001    5  Extended
/dev/sda5               1       60801   488383969+   7  HPFS/NTFS

Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x72452000

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19552   157051408+  83  Linux
/dev/hda2           19553       19929     3028252+   5  Extended
/dev/hda5           19553       19929     3028221   82  Linux swap / Solaris

Disk /dev/hdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd989d989

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       19930   160084940+   7  HPFS/NTFS


Hope that tells you what you are looking for...

Oh, The 500Gig you see is a SATA drive, which is working fine.

---

### Post by p_quarles on 2008-01-16
Hmm. It says there that you have three hard drives -- sda, hda, and hdb. Is this the case? Which one is it that you are trying to mount in Linux? (hda is the one that's already mounted -- sda would be a SATA drive, and hdb would be an IDE).

---

### Post by Rwild on 2008-01-16
It has to be the hdb as I can view the SATA drive with no issues whatsoever.

---

### Post by p_quarles on 2008-01-16
Okay. First, you'll need to get the UUID of hdb, which can be obtained by running this command:
```
ls -l /dev/disk/by-uuid
```
Make a note of the UUID for hdb. 

Now, make a mount point for the NTFS disk:
```
sudo mkdir /media/whatever
```

Then, you'll need to edit the fstab (filesystem table):
```
sudo nano /etc/fstab
```
Add a line to the end, like this:
```
UUID /media/<mount point>     ntfs-3g     defaults,locale=en_US.utf8   0    0
```
This should cause the disk to mount when you boot up. If it doesn't, post back. If it does, we can look at the CD drive problem.

---

### Post by Rwild on 2008-01-16
How do I save and exit the terminal once I modify?

---

### Post by p_quarles on 2008-01-16
In Nano? The "^" characters next to the options stand for the ctrl key. So, exit is ctrl-x. I can't remember the exact option to save, but the menu should indicate it.

---

### Post by Rwild on 2008-01-16
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=7f8a30af-e3f4-4422-bab8-64a405f05de7 /               ext3    defaults,erro$
# /dev/hda5
UUID=b0200b0c-759c-43cc-bfba-92e666590ae7 none            swap    sw           $
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
UUID /media/4494F35094F3434A     ntfs-3g     defaults,locale=en_US.utf8   0    0


That's what it looks like now... I rebooted and nothing has changed...  Did I do everything right?

---

### Post by p_quarles on 2008-01-16
> **Rwild said:**
> That's what it looks like now... I rebooted and nothing has changed...  Did I do everything right?
Not quite. The mount point and the UUID are two different things. I would make a mount point that's easier to remember, honestly, and then reconfigure the last line to look like this:
```
UUID=4494F350943434A /media/mountpoint ntfs-3g defaults,locale=en_US.utf8 0 0
```

---

### Post by Rwild on 2008-01-16
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=7f8a30af-e3f4-4422-bab8-64a405f05de7 /               ext3    defaults,erro$
# /dev/hda5
UUID=b0200b0c-759c-43cc-bfba-92e666590ae7 none            swap    sw           $
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
UUID=4494F350943434A /media/whatever ntfs-3g defaults,locale=en_US.utf8 0 0

Is that last line right now?  Nothing is coming up...

---

### Post by p_quarles on 2008-01-16
> **Rwild said:**
> Is that last line right now?  Nothing is coming up...
Well, are you sure you got the UUID right? Can you post the results you got from:
```
ls -l /dev/disk/by-uuid
```

---

### Post by Rwild on 2008-01-16
```
root@rwild-desktop:~# ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2008-01-16 15:43 10D8-132E -> ../../sdb1
lrwxrwxrwx 1 root root 10 2008-01-16 15:43 4494F35094F3434A -> ../../hdb1
lrwxrwxrwx 1 root root 10 2008-01-16 15:43 4BFD5DC91E09E4B5 -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-01-16 15:43 7f8a30af-e3f4-4422-bab8-64a405f05de7 -> ../../hda1
lrwxrwxrwx 1 root root 10 2008-01-16 15:43 b0200b0c-759c-43cc-bfba-92e666590ae7 -> ../../hda5
root@rwild-desktop:~#
```

hdb1 is the mount point I was after right?

---

### Post by p_quarles on 2008-01-16
Are you certain the disk isn't mounted? What's the output of this?:
```
ls -al /media/whatever
```

---

### Post by Rwild on 2008-01-16
```
root@rwild-desktop:~# ls -al /media/whatever
total 8
drwxr-xr-x 2 root root 4096 2008-01-16 14:53 .
drwxr-xr-x 8 root root 4096 2008-01-16 15:51 ..
```

Is the disk "Filesystem" hda?  And is the other IDE drive I can view in "computer" the drive we are trying to mount?  When I click on the IDE drive I can see in "Computer", it says it is unable to mount due to an unclean shutdown in Windows... 

I installed over Vista and obviously didn't do a proper shut down...:mad:

[http://img152.imageshack.us/img152/185/screenshotgnomemountfj8.png](http://img152.imageshack.us/img152/185/screenshotgnomemountfj8.png)

---

### Post by p_quarles on 2008-01-16
> **Rwild said:**
> ```
root@rwild-desktop:~# ls -al /media/whatever
total 8
drwxr-xr-x 2 root root 4096 2008-01-16 14:53 .
drwxr-xr-x 8 root root 4096 2008-01-16 15:51 ..
```

Is the disk "Filesystem" hda?  And is the other IDE drive I can view in "computer" the drive we are trying to mount?  When I click on the IDE drive I can see in "Computer", it says it is unable to mount due to an unclean shutdown in Windows... 

I installed over Vista and obviously didn't do a proper shut down...:mad:

[http://img152.imageshack.us/img152/185/screenshotgnomemountfj8.png](http://img152.imageshack.us/img152/185/screenshotgnomemountfj8.png)
I would guess the other computer in the menu is the drive in question. Assuming you still have Windows installed, can you boot that up, and see if it needs to run chkdsk (or whatever it's called)?

---

### Post by Rwild on 2008-01-16
No, I removed it completely as my mobo doesn't have all the necessary drivers for Vista as it is 3 years old..........

In the image I linked too, it says I can "force it to mount"?

---

### Post by p_quarles on 2008-01-16
Yeah, I guess you'll have to add "force" to fstab in the way it suggests. Without a Windows box to fix it, probably no other option. 

A question, though: is there currently any data on this disk? If so, is it backed up elsewhere? I ask because if you're not using Windows, it might be a good idea to reformat this disk to ext3.

---

### Post by Rwild on 2008-01-16
Unfortunatly, not at the moment... I'm not exactly sure what ext3 means, but once I get it mounted, can I format it FAT32 so it can be viewable in a Windows environment if I do decide to do a dual boot in a few months?

I guess my main question for you at the moment is how exactly should I write the code for the line to force?  Where should it go?  Sorry, still learning and not very sure of myself in terminal.

---

### Post by p_quarles on 2008-01-16
It would look like this:
```
 UUID=4494F350943434A /media/whatever ntfs-3g defaults,locale=en_US.utf8,force 0 0
```
ext3 = the default filesystem used in many Linux distros, including Ubuntu. 
NTFS = the filesystem introduced by Windows NT, and subsequently adopted in Win 2K, XP and Vista.
FAT32 = very old, inefficient and inflexible filesystem. 

So, if you're going to use Windows in the future, I would suggested leaving the disk with its current filesystem. The only advantage of FAT32 is that it can be read by anything without much trouble. Since Linux can now read and write to an NTFS system, though, the only reason to use FAT32 would be if you were going to hook the disk up to a Macintosh or a Windows 98 machine.

---

### Post by Rwild on 2008-01-16
Oh wow.  Thanks for the run down on formats... :D

So, I just replaced the last line of code and restarted.  Once rebooted, I clicked on the drive and it asked for a password.  Once I entered my password, the same message popped up about an improper Windows shutdown.  

So, I go check my sudo nano /etc/fstab to see everything is blank...  Do you have any other ideas or should I just call up a friend and see if I can drop my drive in his box?

---

### Post by p_quarles on 2008-01-16
The entire thing is blank?!? That's puzzling.

I would try something else first. Make sure that the GUI for ntfs-3g is installed:
```
sudo apt-get install ntfs-config
```
Then, run that and follow its instructions. This will generate a new /etc/fstab file, and it's worked fine in my experience. 

If it doesn't appear in your menu for whatever reason, you'll need to run it from the command line:
```
gksudo ntfs-config &
```

---

### Post by Rwild on 2008-01-16
Oh, and when I try to type in the code verbatim from the window that pops up, it says that only root can do that... And I'm not root... :(

---

### Post by p_quarles on 2008-01-16
> **Rwild said:**
> Oh, and when I try to type in the code verbatim from the window that pops up, it says that only root can do that... And I'm not root... :(
You'll need to put "sudo" at the beginning of the command to authenticate as the root user.

---

### Post by Rwild on 2008-01-16
Wow... You have taught me so much just in the last 30 minutes :D

So, I ran your code and restarted after configuration... Then I did this...

```
root@rwild-desktop:~# sudo mount -t ntfs-3g /dev/hdb1 /media/disk -o force
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/disk: No such file or directory
FUSE mount point creation failed
Unmounting /dev/hdb1 ()

```

---

### Post by p_quarles on 2008-01-16
> **Rwild said:**
> Wow... You have taught me so much just in the last 30 minutes :D

So, I ran your code and restarted after configuration... Then I did this...

```
root@rwild-desktop:~# sudo mount -t ntfs-3g /dev/hdb1 /media/disk -o force
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/disk: No such file or directory
FUSE mount point creation failed
Unmounting /dev/hdb1 ()

```
You need to replace the mount point in the command (/media/disk) with the directory you actually want to use. If I recall, it was /media/whatever

---

### Post by Rwild on 2008-01-16
It worked!  Thanks so much... My etc/fstab doesn't exist, but I don't think that matters... At the moment anyways.

So, do you have time to help me tackle this issue I am having my optical drives or no?

Both drives work... As when I place a disk in either, both will have a window which pops up on the screen.  So, I guess it's not a huge issue.  I just don't understand why only one would show itself in "Computer".

---

### Post by p_quarles on 2008-01-16
The "computer" folder is controlled by Nautilus, so changing it would likely involve using the gconf-editor. Unfortunately, I haven't used Gnome in quite some time, so I don't know exactly what you would do. If it were my computer, though, I probably wouldn't bother with it if both drives are working.

---

### Post by Rwild on 2008-01-16
Alright, works for me then... If you don't mind me asking, why do you KDE over Gnome?

---

### Post by p_quarles on 2008-01-16
Actually, I use Fluxbox. The reason is just that it's much lighter (than Gnome, KDE or Xfce), and every aspect of the desktop configuration can be controlled with simple text files. It was actually annoying little configuration issues like the one with your CD-ROM drive that led me to use it. Gnome and KDE are both great for what they are, but the fact that they rely on graphical configuration programs makes them more limited (but certainly easier for the vast majority of users, as well).

---

### Post by Rwild on 2008-01-16
Ah makes sense.  Well, thanks for all the tips.  Best of luck with computers in the future!  God knows we all need it. ;)

---

