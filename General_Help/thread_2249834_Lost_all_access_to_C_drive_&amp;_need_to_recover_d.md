---
title: "Lost all access to C drive &amp; need to recover data"
date: 2014-10-24
forum: General Help
---

### Post by netsurfau on 2014-10-24
FML

I'm running 14.04 on a AMD Quad Core with 4Gb RAM.

My system has been getting progressively flaky for a while, with odd little issues that were more annoying than anything else.

Yesterday an update for Time-zones failed to install, which seemed a bit strange.  I then tried to start Google Chrome browser, but it wouldn't load.  This has happened before but, I'd worked out a fix.
Because the Shut-down menu had stopped working, I used CTRL+ALT+DEL to bring up the "Log Out/Lock" window.  Instead of getting the expected window, the screen went blank, with just a curser
blinking in the top left corner.  After waiting a couple of minutes without change, I used CTRL+ALT+DEL again.  This caused the system to completely reboot. On the reboot, as Ubuntu was loading, I 
got an error screen saying that it couldn't load because, a number of files in different system directories hadn't closed properly.

I tried accessing the drive by using the "Live" version of 14.04, but still got an error message.  I subsequently installed a fresh version of 14.04 on my "D drive", so I could at least have a working system.
I'm still unable to access "sda", getting the following error message:

**Unable to access "499 GB Volume"**

Error mounting /dev/sda1 at /media/luke/43908c55-e220-4ea7-acf4-01732be278b9: Command-line `mount -t "ext4" -o 
"uhelper=udisks2,nodev,nosuid" "/dev/sda1" "/media/luke/43908c55-e220-4ea7-acf4-01732be278b9"' 
exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I desperately need to recover my Home directory as it has around 250GB of data.  Some of which I cannot afford to lose.

---

### Post by dragonfly41 on 2014-10-25
"bad superblock on /dev/sda1" points to a corrupted disk.

> 
... as it has around 250GB of data. Some of which I cannot afford to lose. 


If at all possible create a clone of your disk image onto another fresh disk (perhaps an external USB drive) before going much further so that you have a backup of your 250GB of important data .. even with the bad superblock in the copy.

Then you can attempt to recover superblock following steps in this article (and other like articles) .. just search "bad superblock":-

[http://unix.stackexchange.com/questions/33284/recovering-ext4-superblocks](http://unix.stackexchange.com/questions/33284/recovering-ext4-superblocks)

testdisk is a tool used for such recovery.

---

### Post by Mark Phelps on 2014-10-25
You mention "C drive" and "D drive" -- but these are MS Windows terms, not Linux terms.  Your error message indicates a Linux filesystem on the drive, not MS Windows filesystem.

So which it is -- MS Windows or Linux?

---

### Post by netsurfau on 2014-10-25
Unfortunately I don't have a spare 500Gb drive.  My system has two 500Gb drives & it's the second one I'm using currently as my working drive.

I have Gparted installed on this partition & have used it successfully in the past to recover drives.  Will it do the same as testdisk?

---

### Post by netsurfau on 2014-10-25
It is Linux.  I started with MS long before coming over to Linux & still support people with MS systems.  Which tends for me to "cross talk" terminology occasionally.

sda is the corrupted drive & sdb is the one I'm using to have a working system.

---

### Post by oldfred on 2014-10-25
Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[xhttp://kember.net/articles/reisub-the-gentle-linux-restart/](xhttp://kember.net/articles/reisub-the-gentle-linux-restart/)

    
I would first try fsck, but since booting from another system, you do not need live install, just make sure not mounted which it is with the errors.

 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

Then if that does not work, recovery of superblock or other aggressive repairs may be required. Each has more risk of losing data so copy/backup is essential. If data was that valuable in the first place a good backup procedure is required as drives do fail, users make mistakes and things just happen.

---

### Post by netsurfau on 2014-10-26
@oldfred,

These are the results from trying the two commands you suggested.  Ideas?

luke@luke-recovery:~$ sudo e2fsck -c -p -f -v /dev/sda
[sudo] password for luke: 
e2fsck: Bad magic number in super-block while trying to open /dev/sda
/dev/sda: 
The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

luke@luke-recovery:~$ sudo e2fsck -f -y -v /dev/sda
e2fsck 1.42.9 (4-Feb-2014)
ext2fs_open2: Bad magic number in super-block
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

---

### Post by oldfred on 2014-10-26
You do not run it on a drive like sda, but on a partition like sda1 or sda5. 

It only works on ext2, ext3 or ext4 formatted partitions. If you have more than one ext formatted partition, you may need to run e2fsck on all of them separately.

---

### Post by netsurfau on 2014-10-26
@oldfred,

I ran the commands again using sda1, and the second one repaired the drive.  Reading through the list of fixes, it looks like none of my data files were damaged.

I'm just about to back up my Home directory to a spare partition, then I'm going to wipe sda1 and do a clean install of 14.04 on it.

Thank you for saving me from a world of grief.  If I had a friend in Chicago, I'd be organising them to buy you a beer or three.

Again, thank you.


Please mark this thread as closed.

---

### Post by oldfred on 2014-10-26
Glad that worked. :)

You can change it to solved yourself.

I am in Fla this week, but next time I am in your town I will be glad to toast one together.

---

### Post by netsurfau on 2014-10-26
I live in Canberra, Australia.  So, if you ever decide to visit this beautiful city, I will gladly show you around.

Do need help with one more thing.

How do I change the permissions for my other partitions?  My memory for command line changes is rather poor. 
Both the now repaired one & my spare partition are owned by "root", and I need to change them over to "luke", so 
I can copy my Home directory over.

---

### Post by oldfred on 2014-10-27
For Linux format partitions only, (if NTFS then only the mount in fstab controls it and root usually still owns it but you can then use it).

 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data

Usually better to permanently mount in fstab:
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.



Never been to that part of the world, maybe someday?

---

