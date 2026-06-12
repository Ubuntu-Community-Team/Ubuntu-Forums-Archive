---
title: "fstab is fs-frustrating"
date: 2008-01-19
forum: General Help
---

### Post by TheMann00 on 2008-01-19
I had another post on here a while back about mounting my IDE drive via FSTab- but I think I have confused others, and also myself.  While all the advice is good advice, it doesn't seem to be addressing my core issue- so here is a complete run-down of what I've done, and what isn't working:

Reinstalled Ubuntu- for reasons other than this HDD issue, but thought it might also fix that in the meantime.  It did not.  On a fresh install, I log in, and I see my USB drive properly displayed on my desktop.  I can browse through it, and read/write/delete.  Everything is working on it.

Ubuntu is installed on an 80GB SATA drive.  Additionally, I have a 500GB IDE drive, which I refer to as my Media Drive.  It has all my downloads, music, movies, tv shows, etc etc etc etc.  Nothing but storage.  I can get to it on my fresh install:  Places>Computer - then either double-click on Media Drive, or right-click:mount.  I have to enter my password, and it mounts the drive for me, and puts a link to it on my desktop.  If I leave it manually mounted, and restart- it's gone (as expected) 

sidenote- the boot drive in *fdisk -l* looks a little weird, but that is another issue for another day- this problem I'm trying to deal with existed before that- so just ignore it please)

When not mounted, running *sudo fdisk -l *gives me the following (color coded, you'll see why later): 
[INDENT][COLOR="Red"]Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x109a109a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4714    37865173+  83  Linux
/dev/sda2            9157        9729     4602622+   5  Extended
/dev/sda3   *        4715        9156    35680365   83  Linux
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris
/dev/sda6            9157        9352     1574307   82  Linux swap / Solaris

Partition table entries are not in disk order[/COLOR]
[COLOR="Lime"]
Disk /dev/hdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5553dc55

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       60801   488384001    7  HPFS/NTFS[/COLOR]

[COLOR="Blue"]Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS[/COLOR][/INDENT]


When I run *sudo /sbin/vol_id -u /dev/hdd1 - I* get the following
[INDENT]ACE0777AE0774A1A[/INDENT]

So- now I create a mount point: 
[I]sudo mkdir /mnt/MediaDrive
sudo chmod 777 /mnt/MediaDrive[/I]

And I add the following line to my fstab:
*UUID=ACE0777AE0774A1A 	/mnt/MediaDrive 	ntfs		defaults	0	0*

Now back in terminal, I type *sudo mount -a* -- and I get no errors.  The Media Drive shows up on my desktop, and I can read/write/delete all files on the drive.  Sounds like I've got it setup correctly!  Let's reboot!

Uh-oh.  After reboot, no Media Drive.  Not on my desktop, not in Places.  When I go to Places>Computer - it is no longer listed here either.  I can't even manually mount it.  The only way I ever get it back is when I remove that line (or comment it out) of fstab.  While the drive isn't there, I run *sudo fdisk -l *again, and get the following output:
[INDENT][COLOR="Lime"]Disk /dev/hdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5553dc55

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       60801   488384001    7  HPFS/NTFS[/COLOR]

[COLOR="Red"]Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x109a109a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4714    37865173+  83  Linux
/dev/sda2            9157        9729     4602622+   5  Extended
/dev/sda3   *        4715        9156    35680365   83  Linux
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris
/dev/sda6            9157        9352     1574307   82  Linux swap / Solaris

Partition table entries are not in disk order[/COLOR]

[COLOR="Blue"]Disk /dev/sdf: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       30401   244196001    7  HPFS/NTFS[/COLOR][/INDENT]

Now- I notice that the order of my drives have changed.  Not sure what this means, or what I can do about it, but that is the ONLY thing I can find from what I have told you.

I'd really like to have this drive come up automatically, because I plan to re-share it so I can watch movies on my Xbox the way I did when I had WindowsXP.

---

### Post by TheMann00 on 2008-01-20
Oh comon- no takers at all?  No ideas??

---

### Post by TheMann00 on 2008-01-20
Well, I'm still struggling with this issue.  This could be the deal-breaker for me.  That drive really needs to be automatically mounted, and shared on the network.  If Ubuntu can't do that... I'll have to find something that can or go back to that other OS.  Please advise!  Any help or a point in the right direction is greatly appreciated!

---

### Post by zero-9376 on 2008-01-20
have you maybe tried just using the /dev/sdXX notation in fstab instead of the uuid based method.

---

### Post by jeffus_il on 2008-01-20
Do I understand you correctly, that you successfully mount a partition using fstab, and then you change to the folder where you mounted it, in this case [I]MediaDrive and there is nothing there?
[/I]

---

### Post by rosegarden78 on 2008-01-20
> **TheMann00 said:**
> Well, I'm still struggling with this issue.  This could be the deal-breaker for me.  That drive really needs to be automatically mounted, and shared on the network.  If Ubuntu can't do that... I'll have to find something that can or go back to that other OS.  Please advise!  Any help or a point in the right direction is greatly appreciated!

EDIT: I'm sorry I mean check the "/dev" folder for Johnny-come-lately, not fstab or mtab, as that's where my LACIE drive shows up.  It'll probably look like sdb1 or something you can use ls commands to look for it.  That's what you need to mount.

sudo mount /dev/sdb1 /mnt

---

### Post by rosegarden78 on 2008-01-20
As far as networking you may need to install Samba shares.  Look for this topic on Ubuntu Forums and more solutions as well.  The only file sharing I do across wifi network is running two Apache servers to exchange files via localhost.

EDIT: I'm not sure what you mean by networking but you can use XP in VirtualBox and it networks with Ubuntu.

---

### Post by TheMann00 on 2008-01-20
> **zero-9376 said:**
> have you maybe tried just using the /dev/sdXX notation in fstab instead of the uuid based method.


Did that originally, and switched to UUID at someone's suggestion.  I will attempt to switch back.

---

### Post by TheMann00 on 2008-01-20
> **jeffus_il said:**
> Do I understand you correctly, that you successfully mount a partition using fstab, and then you change to the folder where you mounted it, in this case [I]MediaDrive and there is nothing there?
[/I]

No- after manually mounting, it works fine.
If I unmount it, update fstab as described, I can run a mount -a (invoking the newly saved fstab) and it works fine.  But on a reboot, the drive isn't there, and it isn't even available for manual mounting anymore.

---

### Post by TheMann00 on 2008-01-20
> **TheMann00 said:**
> Did that originally, and switched to UUID at someone's suggestion.  I will attempt to switch back.

Switched my "UUID=<####>" to /dev/hdd1

Same as before- works when I do a mount -a after saving fstab, but does not work after reboot, or even after a reboot and then mount -a then.

---

### Post by TheMann00 on 2008-01-20
> **rosegarden78 said:**
> Note:  /etc/mtab also contains device names from time to time so check it

First plugin your device and run "nano /etc/fstab" then "nano /etc/mtab" and make notes of the contents.
Second unplug your device and run the same two commands.

Note the one line difference between them.  That Johnny-Come-Lately is your device name.  (Such as /dev/sda1 or /dev/sdb1 for peripherals)

If you can mount it by hand using mount and the terminal you can make a shell script.  try putting whatever you typed in a text file with this header:

!#/bin/sh
Your mounting commands here....

Save the file in your /home folder, right click the icon, select properties - permissions and make executable or use terminal and chmod
Now go Menu and choose Settings - Autostart Application
Add a new item to the menu and type this in:

bash /home/nameOfScript

When X starts it calls your script with bash, the interpretor, which executes the commands required to mount your device.  Otherwise you have to mess with runlevels and that gets really ugly.  Stick with executable shell scripts, Startup Programs and keyboard shortcuts using bash.

If this works- my next step will be to share it on the network.  Will my network share properties stay between reboots?  I would think it won't-- but maybe?

---

### Post by jeffus_il on 2008-01-20
> **TheMann00 said:**
> No- after manually mounting, it works fine.
If I unmount it, update fstab as described, I can run a mount -a (invoking the newly saved fstab) and it works fine.  But on a reboot, the drive isn't there, and it isn't even available for manual mounting anymore.

What do you expect to find there. what are the contents of the  /media/MediaDrive folder after a successful mount using fstab?

---

### Post by TheMann00 on 2008-01-20
> **jeffus_il said:**
> What do you expect to find there. what are the contents of the  /media/MediaDrive folder after a successful mount using fstab?
[INDENT]
desktop:/mnt/MediaDrive$ ls
desktop:/mnt/MediaDrive$ [/INDENT]
Looks like there are no contents of /mnt/MediaDrive
What I expect to find is a useable drive.  At a minimum, the drive in unmounted status- but there is nothing at all.  It might as well be un-plugged.

---

### Post by jeffus_il on 2008-01-21
Could you post the output of  ```
mount
``` in the terminal?

---

### Post by TheMann00 on 2008-01-22
> **jeffus_il said:**
> Could you post the output of  ```
mount
``` in the terminal?

When?
When I have the fstab changed to what I think it should be?
When the fstab is changed, and I've rebooted- and then the drive disappears?

As of right now, fstab does not contain any code attempting to load my drive, but I have manually mounted the drive previously:
[INDENT]desktop:~$ mount
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/hdd1 on /mnt/MediaDrive type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
[/INDENT]

Here again after *umount -a*
[INDENT]desktop:~$ mount
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
udev on /dev type tmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)

[/INDENT]

And after adding the code for my drive back to fstab, and doing *mount -a*
[INDENT]desktop:~$ mount
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
udev on /dev type tmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/hdd1 on /mnt/MediaDrive type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
[/INDENT]

---

### Post by wieman01 on 2008-01-22
Would you mind posting your current version of '/etc/fstab'? Please point out which driver you want to have mounted at start-up (e.g. /dev/hdd1), so that I don't confuse anything.

---

### Post by jeffus_il on 2008-01-22
Does the partition /dev/hdd1 contain the files you are looking for?
And is the directory it is mounted at /mrdia/MediaDrive empty of files?

Maybe this is your problem:
> Missing, disappeared files or directories? or Why can't I see all filenames with national characters? or Why do I get "Skipping unrepresentable filename (inode XXXXX) ..." messages?  This means that your operating system (OS) doesn't have the correct language specific  settings (locale, LANG variable, LC_ALL, etc) thus some filenames can't be converted to your language and won't be visible. The reason can be: [LIST]
[*]The locale setting wasn't configured during installation.
[*]Not the correct locale was configured.
[*]The configured value doesn't exist on the system.
[*]The OS configures the setting in a too late stage during          the boot process, only after the NTFS volume was already mounted.[/LIST] The most common explanation is the latter one. This is why unmounting then mounting  such volumes after boot often makes all filenames visible.   Solution: The OS vendor should move the language specific configuration to an earlier  phase to precede the mounts of the NTFS volumes in time. 
 Workaround: ntfs-3g supports the 'locale' mount option which can be used to set  the correct language value. You can see what locales you have on your system by using the following command: 
locale -a If you can't find the preferred setting then you must generate it, which is very distribution dependent. To do so, a package like glibc-i18ndata (openSUSE,  Mandriva, ...) or locales (Debian, Ubuntu, ...) must be installed then enter the below  command as root to generate the language_COUNTRY.UTF-8 locale. For example the  Brazilian is: localedef -i pt_BR -f UTF-8 pt_BR.UTF-8 Then you can use the "locale=pt_BR.UTF-8" option during mount. If some of your softwares are not UTF8 ready then they will not  show correctly the UTF8 filenames. Please consult your distribution documentation about  how to enable full UTF8 support.
 Status: Not ntfs-3g problem. Please ask your OS vendor to fix the boot time configuration problem. 



from:
[http://www.ntfs-3g.org/support.html#plugandplay](http://www.ntfs-3g.org/support.html#plugandplay)

---

### Post by Coombabah on 2008-01-22
> **TheMann00 said:**
> [INDENT]
...
What I expect to find is a useable drive.  At a minimum, the drive in unmounted status- but there is nothing at all.  It might as well be un-plugged.

This is a longshot.
It's not a seagate freeagent go external usb hard drive?
I had missing contents until I turned off it's non-standard spindown after 3 minutes inactivity.
This has to be turned off with (edit: sdparm or) the supplied windows software before it is useful on non-windows OSes.

---

### Post by bodhi.zazen on 2008-01-22
How to fstab : [http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by TheMann00 on 2008-01-22
> **wieman01 said:**
> Would you mind posting your current version of '/etc/fstab'? Please point out which driver you want to have mounted at start-up (e.g. /dev/hdd1), so that I don't confuse anything.

[INDENT]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=30f4f9c6-c4d6-4c5e-a91f-90e7855d6e1f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=d0f3ce8a-a8b8-4adb-83ca-f72f8ddeba64 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

#MEDIA DRIVE
/dev/hdd1 	/mnt/MediaDrive 	ntfs		defaults	0	0[/INDENT]

---

### Post by TheMann00 on 2008-01-22
> **jeffus_il said:**
> Does the partition /dev/hdd1 contain the files you are looking for?
And is the directory it is mounted at /mrdia/MediaDrive empty of files?

Maybe this is your problem:


from:
[http://www.ntfs-3g.org/support.html#plugandplay](http://www.ntfs-3g.org/support.html#plugandplay)


No-- it's not missing files.  It's missing drive.
When I boot, and have no mention of my media drive in *fstab-* I get this:
[IMG]http://www.katyandjacob.com/images/forumcontent/ubuntu/mediadrive.gif[/IMG]


When I add a line in *fstab,* and CONFIRM that it works by doing *mount -a*-- I reboot and get this:
[IMG]http://www.katyandjacob.com/images/forumcontent/ubuntu/nomediadrive.gif[/IMG]

---

### Post by TheMann00 on 2008-01-22
> **Coombabah said:**
> This is a longshot.
It's not a seagate freeagent go external usb hard drive?
I had missing contents until I turned off it's non-standard spindown after 3 minutes inactivity.
This has to be turned off with the supplied windows software before it is useful on non-windows OSes.

Nope- internal IDE drive.

---

### Post by jeffus_il on 2008-01-23
You do no see the fstab mounts in nautilus, you don't see any fstab partitions, you have the correct behavior of the system. You also don't see the root partition. Only removable media show up in the browser, mounted media are accessed through the file system.

---

### Post by wieman01 on 2008-01-23
> **TheMann00 said:**
> 
#MEDIA DRIVE
/dev/hdd1 	/mnt/MediaDrive 	ntfs		defaults	0	0
This looks actually fine. Have you created the folder yet?
> sudo mkdir /mnt/MediaDrive
I am pretty sure '/dev/hdd1' is mounted at start-up. The contents of 'fstab' are definitely OK. After a reboot please post:
> sudo fdisk -l
> sudo df -l

_**EDIT:**_
A good reference by the way: [http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

---

### Post by jeffus_il on 2008-01-23
I sure the system is OK, he is just expecting nautilus to show icons for fstabbed file systems which it does not do, he has to access them thru the file system /media/whatever.

---

### Post by TheMann00 on 2008-01-24
> **jeffus_il said:**
> I sure the system is OK, he is just expecting nautilus to show icons for fstabbed file systems which it does not do, he has to access them thru the file system /media/whatever.

So you are saying, after fstab runs this line:
[INDENT]#MEDIA DRIVE
/dev/hdd1 	/mnt/MediaDrive 	ntfs		defaults	0	0[/INDENT]
I open up /mnt/MediaDrive to see my files?

---

### Post by TheMann00 on 2008-01-24
> **TheMann00 said:**
> So you are saying, after fstab runs this line:
[INDENT]#MEDIA DRIVE
/dev/hdd1 	/mnt/MediaDrive 	ntfs		defaults	0	0[/INDENT]
I open up /mnt/MediaDrive to see my files?

Yup- that works.
Why is it after adding the line to **fstab,** *mount -a* will put an icon on my **desktop,** and also in **places?**  That was my biggest confusion.  I knew I had the code right, but after a reboot, my confirmation was gone.

Where do I go about permanently sharing out /mnt/MediaDrive now?  Is that easily accomplished with samba share (someone mentioned earlier?)

---

### Post by TheMann00 on 2008-01-24
> **wieman01 said:**
> This looks actually fine. Have you created the folder yet?

I am pretty sure '/dev/hdd1' is mounted at start-up. The contents of 'fstab' are definitely OK. After a reboot please post:


As requested: (this is with my fstab set to load the drive to /mnt/MediaDrive)
[INDENT][COLOR="Red"]desktop:~$ sudo fdisk -l[/COLOR]

Disk /dev/hdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5553dc55

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x109a109a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2            9157        9729     4602622+   5  Extended
/dev/sda3   *        4715        9156    35680365   83  Linux
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris
/dev/sda6            9157        9352     1574307   82  Linux swap / Solaris

Partition table entries are not in disk order
[COLOR="Red"]desktop:~$ sudo df -l[/COLOR]
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3             35119976   8276644  25059316  25% /
varrun                  517724        88    517636   1% /var/run
varlock                 517724         0    517724   0% /var/lock
udev                    517724       100    517624   1% /dev
devshm                  517724         0    517724   0% /dev/shm
lrm                     517724     34696    483028   7% /lib/modules/2.6.22-14-generic/volatile
/dev/hdd1            488384000 242553396 245830604  50% /mnt/MediaDrive[/INDENT]

---

### Post by TheMann00 on 2008-01-25
> **TheMann00 said:**
> Yup- that works.
Why is it after adding the line to **fstab,** *mount -a* will put an icon on my **desktop,** and also in **places?**  That was my biggest confusion.  I knew I had the code right, but after a reboot, my confirmation was gone.

Where do I go about permanently sharing out /mnt/MediaDrive now?  Is that easily accomplished with samba share (someone mentioned earlier?)


So--- for the lazy man.  Now that I realize my files are all showing up in /mnt/MediaDrive - How do I get an icon to show up for that on my desktop, or in places?  Like it used to when I would manually mount?

---

### Post by dcstar on 2008-01-25
> **TheMann00 said:**
> So--- for the lazy man.  Now that I realize my files are all showing up in /mnt/MediaDrive - How do I get an icon to show up for that on my desktop, or in places?  Like it used to when I would manually mount?

Make a link and put the link on your desktop.

---

### Post by rosegarden78 on 2008-01-29
I edited my previous posts to reflect accuracy ... my LACIE shows up in /dev/sdb1 not /etc/fstab or /etc/mtab.  You can mount something like "sudo mount /dev/sdb1 /mnt" and use the mnt folder to browse it.  Don't know about networking per se but like I said VirtualBox networks with Ubuntu and runs all Windows programs except video games.

---

