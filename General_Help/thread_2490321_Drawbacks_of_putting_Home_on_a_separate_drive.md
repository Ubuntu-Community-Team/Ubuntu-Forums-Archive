---
title: "Drawbacks of putting /Home on a separate drive?"
date: 2023-08-30
forum: General Help
---

### Post by Advait on 2023-08-30
Currently running 21.04. I'm thinking of upgrading to 22.04. What are the drawbacks of putting /Home on a separate internal nvme drive? I'm not a technical person and know nothing about terminal commands, so if doing that will cause problems then I won't do it. I only have the skills to troubleshoot very simple problems (and sometimes even those are too much for me).

I've got an AMD gaming laptop with 2 internal nvme drive slots. Right now everything is on one nvme (2TB).

Is it easy or hard to successfully install /Home on a separate internal drive? Does it require using  terminal commands?

I'm an average home computer user. No home network. I don't program, don't edit video or audio, not a gamer, not a streamer. I just browse the web, use Syncthing with my Android phone, make data backups and that's about it. 2 or 3 times a year I'll spin up a VM in Virtmanager. That's the limit of my Linux skills.

---

### Post by TheFu on 2023-08-30
21.04 support ended in Jan **2022**.  Please don't be your own worst enemy by running a non-supported release.  I prefer to use LTS releases and only LTS releases.  Those are in April of even years. the next will be 24.04 ... next April.  

Right now, the releases with support are 20.04, 22.04, 23.04 and if you have paid ESM, 18.04 and 16.04.  See the pattern?
Upgrades AFTER a release isn't support are more difficult, unless we do a fresh install.

> Is it easy or hard to successfully install /Home on a separate internal drive? Does it require using terminal commands?
Depends on your skill level. Nobody can answer that for you, but reading your self-description, I'd say no.  For what you do, a used $200 laptop would be fine.  Heck, for what I do, a $305 used laptop (2017 Core i5 + 8GB + 500GB SATA SSD) is fine.

If you have enough storage in the 2TB SSD, it would be smart to have a separate partition for /home, but it doesn't need to be a separate disk.

The output of 
```
lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
```
would be helpful, since the default installation usually isn't exactly the smartest disk layout.

Of course, only you can decide what is and isn't worth the hassle.
By having most of your personal files on a different partition, OS upgrades will have much less risk, assuming you understand the different partitions and know what it is used for during a fresh install.  OTOH, of you prefer to say "Wipe disk and use the entire thing" for a fresh install, then having your HOME on a separate partition or separate disk doesn't really get you anything.

---

### Post by SeijiSensei on 2023-08-30
Since most of the Linux system files take up less than 30 GB, a 2 TB storage device is certainly adequate. If you have a single Linux filesystem on this device, /home will reside there as well. Follow TheFu's advice and upgrade to a release with "long-term support" like 22.04. The next one, 24.04, will appear in April. Don't worry about having a separate /home.

I've built machines where I had multiple operating systems that I could boot. I would sometimes install a development version of Linux in a separate partition. Having a separate /home partition was useful in that setting since it would be available regardless of which OS I booted. Now I just use virtual machines instead.

---

### Post by Advait on 2023-10-13
> **TheFu said:**
> 21.04 support ended in Jan **2022**.  Please don't be your own worst enemy by running a non-supported release.  I prefer to use LTS releases and only LTS releases.  Those are in April of even years. the next will be 24.04 ... next April.  

I checked and I'm actually on 22.04. Surprised me. I don't know how that happened. I never clicked on "Upgrade". Oh, well. It's no problem. My system is running fine. Although I am curious how I got upgraded to 22.04? It's a mystery.

---

### Post by Advait on 2023-10-13
> **TheFu said:**
> The output of 
```
lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
```
would be helpful, since the default installation usually isn't exactly the smartest disk layout.

Sure, here it is:

```
advait@advait-Bravo-15-A4DDR:~$ lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
NAME        TYPE FSTYPE   SIZE FSAVAIL FSUSE% LABEL MOUNTPOINT
nvme1n1     disk          1.8T                      
&#9500;&#9472;nvme1n1p1 part vfat     512M                      
&#9492;&#9472;nvme1n1p2 part ext4     1.8T  206.1G    84%       /
nvme0n1     disk        476.9G                      
&#9500;&#9472;nvme0n1p1 part vfat      94M   86.5M     7%       /boot/efi
&#9492;&#9472;nvme0n1p2 part ext3   476.8G                      
advait@advait-Bravo-15-A4DDR:~$ 
```

Anything interesting here?

---

### Post by Advait on 2023-10-14
> **TheFu said:**
> By having most of your personal files on a different partition, OS upgrades will have much less risk, assuming you understand the different partitions and know what it is used for during a fresh install.  OTOH, of you prefer to say "Wipe disk and use the entire thing" for a fresh install, then having your HOME on a separate partition or separate disk doesn't really get you anything.

Let me know if I'm missing something, but here's my understanding:

* If I have /home and all my user files on a separate drive then I can easily nuke and pave the system drive without needing to re-copy all my files back on the drive. I have about 1.2TB of user files and it would take many hours to copy all those files back onto the system drive. With /home on a separate drive I don't have to do that. Would save me A LOT of time and hassle.

* I'm assuming that if I wipe out my system drive and re-install, that it's pretty easy to tell the new system that my /home directory is on a separate drive. Is that assumption correct?

* I'm assuming that if I have /home on a separate drive, the system will be ok with that and will behave normally. Is that assumption correct?

* I'm assuming that if I have /home on a separate drive, it won't cause any weird problems. Is that assumption correct? Does having /home on a separate drive cause weird problems? Does the OS not like having /home on a separate directory? If yes, why?

I want to understand the possible problems before doing this.

Because I'm a noob, I would probably hire an Upwork Linux expert to guide me when I do this. But if having /home on a separate directory will cause weird problems, then I won't do it.

I'm a very basic user. I just do browsing, Zoom calls and a few LibreOffice spreadsheets. That's it. I don't do video editing or audio editing or programming or any gaming or any streaming.

---

### Post by MAFoElffen on 2023-10-14
> **Advait said:**
> Sure, here it is:

```
advait@advait-Bravo-15-A4DDR:~$ lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
NAME        TYPE FSTYPE   SIZE FSAVAIL FSUSE% LABEL MOUNTPOINT
nvme1n1     disk          1.8T                      
&#9500;&#9472;nvme1n1p1 part vfat     512M                      
&#9492;&#9472;nvme1n1p2 part ext4     1.8T  206.1G    84%       /
nvme0n1     disk        476.9G                      
&#9500;&#9472;[COLOR=#ff0000]nvme0n1p1 part vfat      94M   86.5M     7%       /boot/efi[/COLOR]
&#9492;&#9472;[COLOR=#ff0000]nvme0n1p2 part ext3   476.8G[/COLOR]                      
advait@advait-Bravo-15-A4DDR:~$ 
```

Anything interesting here?
What OS'es do you have installed?

ext3 has not been a default in many years. 86.6MB for and EFI partition is tiny... Yet you have another vfat partition on the other drive(?) Just trying to figure out what I'm looking at there.

---

### Post by Advait on 2023-10-14
> **SeijiSensei said:**
> Don't worry about having a separate /home.

But if I have /home on a separate drive, then I can wipe out and reinstall my system OS drive without needing to copy all my user files back onto the system drive. I have 1.2TB of user files and it would take many hours to copy all those back onto the system drive. If /home is on a separate drive, then I don't have to bother with all that wasted time and hassle.

Am I missing something?

Does Ubuntu have problems if /home is on a separate drive?

I'm a very basic user. I just do browsing, Zoom calls and a few LibreOffice spreadsheets. That's it. I don't do video editing or audio editing or programming or any gaming or any streaming.

I don't use a NAS or anything like that.

---

### Post by Advait on 2023-10-14
> **MAFoElffen said:**
> What OS'es do you have installed?

ext3 has not been a default in many years. 86.6MB for and EFI partition is tiny... Yet you have another vfat partition on the other drive(?) Just trying to figure out what I'm looking at there.

I'm using Ubuntu 22.04 on my main 2TB system drive.

The other drive has Ubuntu 21.04 but I'm not using it for anything. You can ignore that drive. I don't know why it has an ext3 partition.

If and when I switch to having /home on a separate drive, then the 500GB drive will be the system /root drive. And the 2TB drive will become the /home drive. That's my plan but let me know if there's something better.

---

### Post by MAFoElffen on 2023-10-14
You had a thread on backups right? You took a good backup?

So you have lots of room to re-install "with a separate home", without having to re-copy anything over from your existing home...  You would have to reorganize what is there... Which would require that you followed directions "very carefully."

Basically:
Boot from an installer LiveUSB.

Delete all your folders "other than home" from partition /dev/nvme1n1p2.

Move the User home folder (the folder named after your user name) from inside /home, down to the root of that partition. 

Once confirmed that everything is there, and that /home is empty, then delete the /home folder... That is your new /home folder.

Then start the installer. At the type of panel, select the "other" option to start the partitioner.

Select /dev/nvme1n1, change, and format as vfat EFI. make sure that is select as the boot device in the bottom of the partitioner.

Delete all the partitions from /dev/nvme0n1. 

Select the unused space on /dev/nvme0n1 to create a root partition. Make it anywhere around 60 MB or larger. Use as ext4 and mount at "/" and 
using the vfat partition on /dev/nvme1n1, then using the rest of /dev/nvme0n1 as "/"

Select /dev/nvme1n1. Change. Ensure the format box IS NOT CHECKED. Use as "/home"...

Continue the install. 
--------------------------
I would solicit advise from others on what they think about that before trying it though.

---

### Post by Advait on 2023-10-14
> **MAFoElffen said:**
> You had a thread on backups right? You took a good backup?

Yep, I make daily backups of all my user files to various external drives. And once every few days I do a Clonezilla backup of the whole drive to an external drive.

> **MAFoElffen said:**
> So you have lots of room to re-install "with a separate home", without having to re-copy anything over from your existing home...  You would have to reorganize what is there... Which would require that you followed directions "very carefully."

Basically:
Boot from an installer LiveUSB.

Delete all your folders "other than home" from partition /dev/nvme1n1p2.

Move the User home folder (the folder named after your user name) from inside /home, down to the root of that partition. 

Once confirmed that everything is there, and that /home is empty, then delete the /home folder... That is your new /home folder.

Then start the installer. At the type of panel, select the "other" option to start the partitioner.

Select /dev/nvme1n1, change, and format as vfat EFI. make sure that is select as the boot device in the bottom of the partitioner.

Delete all the partitions from /dev/nvme0n1. 

Select the unused space on /dev/nvme0n1 to create a root partition. Make it anywhere around 60 MB or larger. Use as ext4 and mount at "/" and 
using the vfat partition on /dev/nvme1n1, then using the rest of /dev/nvme0n1 as "/"

Select /dev/nvme1n1. Change. Ensure the format box IS NOT CHECKED. Use as "/home"...

Continue the install. 
--------------------------
I would solicit advise from others on what they think about that before trying it though.

Very interesting. Let me make sure I understand. So at the successful end of this process, my 500GB drive (nvme0n1) will be the OS system root drive with the new OS and all the usual OS files and OS directory structure. 

And my 2TB drive (nvme1n1) will have my /home directory. And the OS on nvme0n1 will happily interact with the /home directory on the nvme1n1 separate drive. 

I got this right?

(and before doing this I would make multiple backups of everything to be safe)

---

### Post by MAFoElffen on 2023-10-14
Yes, exactly. 

Like I said, before hand, you would have to prepare that original partition with your existing user home directory so that the user home directory(s) are in the root of that partition (alone). Because when it mounts as a separate home, then it mounts that partition into the filesystem at /home. So then from there, it finds the user home folders under that in the completed mount.

Those "moves" would be in seconds, because the data itself doesn't really move anywhere. It's in the same partition, so it just resolves where the inodes are to reference them.

That would get you to what you said your end goal is right?

---

### Post by Advait on 2023-10-14
> **MAFoElffen said:**
> Yes, exactly. 

Like I said, before hand, you would have to prepare that original partition with your existing user home directory so that the user home directory(s) are in the root of that partition (alone). Because when it mounts as a separate home, then it mounts that partition into the filesystem at /home. So then from there, it finds the user home folders under that in the completed mount.

Those "moves" would be in seconds, because the data itself doesn't really move anywhere. It's in the same partition, so it just resolves where the inodes are to reference them.

That would get you to what you said your end goal is right?

Yes, looks like it would get me to my end goal. Great!

---

### Post by Advait on 2023-10-14
> **MAFoElffen said:**
> So you have lots of room to re-install "with a separate home", without having to re-copy anything over from your existing home...  You would have to reorganize what is there... Which would require that you followed directions "very carefully."

Basically:
Boot from an installer LiveUSB.

Delete all your folders "other than home" from partition /dev/nvme1n1p2.

Move the User home folder (the folder named after your user name) from inside /home, down to the root of that partition. 

Once confirmed that everything is there, and that /home is empty, then delete the /home folder... That is your new /home folder.

Then start the installer. At the type of panel, select the "other" option to start the partitioner.

Select /dev/nvme1n1, change, and format as vfat EFI. make sure that is select as the boot device in the bottom of the partitioner.

Delete all the partitions from /dev/nvme0n1. 

Select the unused space on /dev/nvme0n1 to create a root partition. Make it anywhere around 60 MB or larger. Use as ext4 and mount at "/" and 
using the vfat partition on /dev/nvme1n1, then using the rest of /dev/nvme0n1 as "/"

Select /dev/nvme1n1. Change. Ensure the format box IS NOT CHECKED. Use as "/home"...

Continue the install.

I don't have the knowledge to execute the steps you list. But that's totally not a problem because I can easily hire a Linux expert on Upwork to execute the steps.

If I tried to do it, it would just be a pile of melted smoking circuit boards at the end. :P :biggrin:

Besides, I want the expert to also set up Btrfs and Btrfs auto snapshots on nvme0 (the OS root drive).

Unless there's anything else I should know, I'll mark this thread as Solved. 

Thanks for your clear instructions and polite patience with a noob like me!

---

### Post by MAFoElffen on 2023-10-14
I tend to let 1fallen deal with people on BTRFS. Both of us help users with BTRFS, I think he is better at that with BTRFS. There are not a lot of peopl ehere that know about BTRFS here besides us. And I do mostly ZFS.

But basically when switching to a different File Manager (LVM2, BTRFS, ZFS), that adds another step, where you are going to create the framework for your BTRFS volumes, subvolumes, mount them into your filesystem, then restore the backups you have and are going to take, to "restore"... Yes, I said that. To write the dat fresh into the new filesystem. Then you setup timeshift to do your auto-snapshots.

BTRFS as a File Manager is a layer between the disk and the filesystem, where the data goes... So has to be written fresh on that new filesystem.

---

### Post by Advait on 2023-10-14
> **MAFoElffen said:**
> But basically when switching to a different File Manager (LVM2, BTRFS, ZFS),

I'm confused. I thought Btrfs was a file system and not a file manager. When I think of file manager I think of Nautilus and Dolphin. Am I missing something? I thought Btrfs was a type of file system just like ext4 is a type of file system. Am I missing something?

> **MAFoElffen said:**
> Then you setup timeshift to do your auto-snapshots.

Yep, Timeshift is a good app. I'll also have the Btrfs expert set up the grub-btrfs tool so snapshots also appear in the grub menu.

> **MAFoElffen said:**
> BTRFS as a File Manager is a layer between the disk and the filesystem, where the data goes... So has to be written fresh on that new filesystem.

I assume that the OS root drive (nvme0) can be Btrfs and the separate drive (nvme1) that has /home can be ext4. Is that an OK set up?

---

### Post by MAFoElffen on 2023-10-14
BTRFS is a computer storage format that combines a file system based on the copy-on-write principle with a logical volume manager, developed together. 
BTRFS as a File Manager is a layer between the disk and the filesystem, where the data goes... So has to be written fresh on that new filesystem.

It is not a production grade system and is still thought of as being in the "Experimental" stage.

---

### Post by Advait on 2023-10-14
> **MAFoElffen said:**
> BTRFS is a computer storage format that combines a file system based on the copy-on-write principle with a logical volume manager, developed together. 
BTRFS as a File Manager is a layer between the disk and the filesystem, where the data goes... So has to be written fresh on that new filesystem.
 
Interesting. I'll have to do some more research to wrap my head around the subtleties of Btrfs. So both Btrfs and Nautilus are called "file managers". Interesting. I'll have to get used to that.

> **MAFoElffen said:**
> It is not a production grade system and is still thought of as being in the "Experimental" stage.

That's OK, my therapist also thinks of me as being in the "Experimental" stage.

:P

---

### Post by #&amp;thj^% on 2023-10-14
> **Advait said:**
> 
That's OK, my therapist also thinks of me as being in the "Experimental" stage.

:P
We will get along just fine then...lol
Well just me but I'm not a fan of home on a separate partition.
Here is the layout of my drive I use for BTRFS:
```
ls /media/me/699d6f89-b75b-4863-b523-c2df37612e75/
@  @home  timeshift  timeshift-btrfs

``` 
While there is improvements made with BTRFS on Ubuntu I just don't move my home to it's own  partition.
Now you can kind of get a feel on how it looks:
@=boot and family ie:
```
ls @
bin   dev  home  lib64  opt   root  sbin  sys  usr
boot  etc  lib   mnt    proc  run   srv   tmp  var

```
Peek inside of /home:
```
ls @home
me

```
Note That home and @home point to the same directory:


Because subvolumes aren't backed up when doing snapshots.

Let's say you do a snapshot of @root...

Then you later replace your root with the backup:

In the first case everything works because @home is an independent subvolume just mounted to /home.

In the second case, you replaced your @root with a backup but now have to copy/snapshot a seperate @home-snapshot to it's place in @root (because you just deleted your @home subvolume by overwriting your old @root with a copy missing the @root/home subvolume).

The first version utilizes the fact that subvolumes can be treated as separate file systems and are independent from each other. You can replace your root with a backup or even just boot from the snapshot keeping anything else intact, because it's just mountpoints, while the second versions means you have to manage (nested) subvolumes and their position in your system manually.

It's good practice to separate user and system data, because rolling either one back should not affect the other.

If you use FS/@/home, then snapshot your rootfs, then at a later restore of it would also restore the user data, which is likely not what you want, and can be pretty confusing.

Now if you separate both / and /home into separate subvols, say fs/@ and fs/@home, you can snapshot and revert either without affecting the other.
That at least makes sense to me.

---

### Post by Advait on 2023-10-16
> **1fallen said:**
> If you use FS/@/home, then snapshot your rootfs, then at a later restore of it would also restore the user data, which is likely not what you want, and can be pretty confusing.

Now if you separate both / and /home into separate subvols, say fs/@ and fs/@home, you can snapshot and revert either without affecting the other.
That at least makes sense to me.

Ahhh... Now I remember. A while back I was exploring how I could transition to Btrfs, but turns out a big problem was the /home vs @home issue. For some reasons which I totally can't remember, the /home vs @home issue prevented me from doing what I was thinking of doing with Btrfs. 

When I transition to Btrfs, I'll be using a tech expert from Upwork to help. I made a note to tell the tech helper about this issue so Btrfs will work the way I want.

---

### Post by MAFoElffen on 2023-10-16
What was what you wanted to do in "home" that brang up the "limitations" that prevented you from using BTRFS? Knowing "that" would be nice to know, to help map out a solution for you...

Have you looked into ZFS or LVM2 as volume managers? Both those have snapshots, and can easily do separate homes that are very flexible.

ZFS also does copy-on-write, is production grade, and is very flexible and easy to move around blocks of data.

The problem people face with Linux, is that there are so many choices to do the same things.

---

### Post by #&amp;thj^% on 2023-10-16
> **MAFoElffen said:**
> 
Have you looked into ZFS or LVM2 as volume managers? Both those have snapshots, and can easily do separate homes that are very flexible.

ZFS also does copy-on-write, is production grade, and is very flexible and easy to move around blocks of data.

**_The problem people face with Linux, is that there are so many choices to do the same things_**.

+1 I second the LVM/ext4 or ZFS
This is not meant to confuse you Advait but just a thought:
```
tac /etc/fstab

UUID=F107-662C      	/boot/efi 	vfat      	rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=ascii,shortname=mixed,utf8,errors=remount-ro	0 2
# /dev/nvme1n1p1

UUID=699d6f89-b75b-4863-b523-c2df37612e75	/home     	btrfs     	rw,relatime,ssd,discard=async,space_cache=v2,subvolid=257,subvol=/@home	0 0
# /dev/nvme1n1p2

UUID=699d6f89-b75b-4863-b523-c2df37612e75	/         	btrfs     	rw,relatime,ssd,discard=async,space_cache=v2,subvolid=256,subvol=/@	0 0
# /dev/nvme1n1p2
# <file system> <dir> <type> <options> <dump> <pass>

# See fstab(5) for details.
# Static information about the filesystems.

```
And the ONLY system I run BTRFS on is Arch. (Don't ask why I'll not respond)
```
tac /etc/fstab

UUID=F107-662C      	/boot/efi 	vfat      	rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=ascii,shortname=mixed,utf8,errors=remount-ro	0 2
# /dev/nvme1n1p1

UUID=699d6f89-b75b-4863-b523-c2df37612e75	/home     	btrfs     	rw,relatime,ssd,discard=async,space_cache=v2,subvolid=257,subvol=/@home	0 0
# /dev/nvme1n1p2

UUID=699d6f89-b75b-4863-b523-c2df37612e75	/         	btrfs     	rw,relatime,ssd,discard=async,space_cache=v2,subvolid=256,subvol=/@	0 0
# /dev/nvme1n1p2
# <file system> <dir> <type> <options> <dump> <pass>

# See fstab(5) for details.
# Static information about the filesystems.

```
I have 2 snapshots stored off my main drive:
```
cd /run/media/me/Intel_2tb/ && ls -la | grep @
**[COLOR="#FF0000"]drwxr-xr-x  1 root root  4096 Sep 22 17:54 @[/COLOR]**
drwxrwxr-x  1 me   me       0 Oct 14 11:45 BTRFS Arch BU @ @home
**[COLOR="#FF0000"]drwxr-xr-x  1 root root     0 Sep 18 09:10 @home[/COLOR]**

```
This is my favorite as well
> **MAFoElffen said:**
> it will not protect "you" from "yourself".

My favorite saying lately has been:
[CENTER]*"Just because something is possible, doesn't make it a good idea."*
[/CENTER]

But then again, one of my previous sayings was:
[center]*"Don't worry... I saw this work in a cartoon once."*
[/center]
Priceless :D

---

### Post by MAFoElffen on 2023-10-16
Whatever you do or decide on, the strength and draw to Linux is also it's danger... Freedom and Choice.

It is infinitely customizable by substituting layers and modules (pieces) here and there... A user can make it his/her own. But, being that it allows you to do so many things, it will not protect "you" from "yourself".

My favorite saying lately has been:
[CENTER]*"Just because something is possible, doesn't make it a good idea."*
[/CENTER]

But then again, one of my previous sayings was:
[center]*"Don't worry... I saw this work in a cartoon once."*
[/center]

---

### Post by Advait on 2023-10-18
> **MAFoElffen said:**
> What was what you wanted to do in "home" that brang up the "limitations" that prevented you from using BTRFS? Knowing "that" would be nice to know, to help map out a solution for you...

It was a while back so I don't remember the details. I really appreciate the kind offer, but at this time I'm not ready to do the switch to Btrfs or ZFS. And when I do I'll hire an Upwork Linux expert to do it for me while I watch.

I know that Btrfs has GUIs for doing manual snapshots on Ubuntu (Timeshift) and OpenSuse (Yast).

Is there a GUI snapshot tool for ZFS? If yes, on which distros can this tool run?

---

### Post by Advait on 2023-10-18
> **1fallen said:**
> +1 I second the LVM/ext4 or ZFS
This is not meant to confuse you Advait but just a thought:

Thanks for the details. As I mentioned, I'll hire a Linux expert when I switch to Btrfs or ZFS. I don't have the skills to do it myself.

---

### Post by pbear42 on 2023-10-18
If you are going to hire someone to do the work, I recommend you look into doing a data partition rather than a home partition.  In your case, /home would stay on the main drive and the data partition would go on the other drive.  With this separation, you can do pretty much anything in future with your Linux system and the data partition will still work.  It's also a cleaner split for backup purposes.  Main drawbacks of a data partition are (a) that it's more technically challenging to do (one has to mount the partition, then symlink folders into /home); and (b) when you upgrade the system (generally every two years) you have to redo software config settings, as those were saved in the old home folder.  OTOH, your helper shouldn't find this challenging (if so, get another one) and there's an advantage to clearing out the cobwebs every couple years.  FWIW, it's what I do, and have for many years.

---

### Post by MAFoElffen on 2023-10-18
@pbear22 -- I do both a speparate pool for Data and Home...

My reasoning, is many of my Linux systems have evolved over the past 13 years.

I don't do do-release upgrades... I keep my data and home drives, install a new OS release and do a migration to that newly installed release. Clean and fast.

Zfs internal mounts makes that easy to the dataset within the filesystem wherever I want. Export the pool, import it into the new system with the same filesystem mount tags. Wallah.

---

### Post by MAFoElffen on 2023-10-18
Why not both? That is what I do (separate data & home pools).

Separating it out, makes backups and snapshots very easy...

Traditionally, mounts are for a filesystem within a partition to a mountpoint tag are one for one. LVM, same. Yes you can manipulate that with symlinks, but then it appears in multiple places in the filesystem, which makes backups somewhat entertaining.

1fallen talked about how BTRFS is an overlay... It is sort of like ZFS, but...

ZFS is just "different.". ZFS has an initernal mounting system as an object property. A pool can have  2[SUP]64[/SUP] filesystem datasets... Each can have it's own mountpoint into the filesystem or it can be added as it's entirety, depending how you make the mount. Datasets are hierarchical. You can take a snapshot at any level.

So a pool can have multiple datasets at the same level, and be mounted in multiple different places within the OS filesystem, and never repeat itself. Datasets a can be outside of the dataset hierarchy (but mounted to appear as if it were) to exclude them from a recursive snapshot.

Like I said, ZFS is just "different". Because it is adjustable and flexible, It inspires imagination and forethought, in what you can do with it.

But... Most of ZFS's management is command line. The only tools I know of that are GUI are the web based Scale UI (Scale Out ZFS) of TrueNAS, and BUI of Oracle ZFS Storage Manager (which is non-free and very costly). TrueNAS does say they are based on Debian. But is has no installed Desktop.

---

### Post by pbear42 on 2023-10-18
Nothing wrong with doing both, and I considered mentioning the option, but it does make things a little more complicated.

---

### Post by MAFoElffen on 2023-10-19
I just finished this Worksation, so not much on it yet, But a good example.
```

$ sudo zfs list
...
dpool                                           2.93M   450G       96K  /dpool
dpool/DATA                                       192K   450G       96K  none
dpool/DATA/ubuntu_2204                            96K   450G       96K  /dpool
hpool                                           2.58G   344G      192K  /home
hpool/USERDATA                                  2.58G   344G      192K  none
hpool/USERDATA/ubuntu_2204                      2.58G   344G     2.58G  /home
kpool                                            406G   493G       96K  /kpool
kpool/QEMU-KVM                                   406G   493G       96K  none
kpool/QEMU-KVM/ubuntu_2204                       406G   493G      104K  /kpool
kpool/QEMU-KVM/ubuntu_2204/ISO                   406G   493G      406G  /kpool/ISO
kpool/QEMU-KVM/ubuntu_2204/KVM-VM                 96K   493G       96K  /kpool/KVM-VM
kpool/QEMU-KVM/ubuntu_2204/images                112K   493G      112K  /var/lib/libvirt/images
kpool/QEMU-KVM/ubuntu_2204/libvirt               620K   493G      620K  /etc/libvirt/
...

$ lsblk -e7 -o name,label,mountpoint
NAME        LABEL           MOUNTPOINT
sda                         
...
&#9500;&#9472;sda2      Win_G           /home/mafoelffen/WIN_G
...

```

---

### Post by Advait on 2023-10-19
> **pbear42 said:**
> If you are going to hire someone to do the work, I recommend you look into doing a data partition rather than a home partition.  In your case, /home would stay on the main drive and the data partition would go on the other drive.  With this separation, you can do pretty much anything in future with your Linux system and the data partition will still work.  It's also a cleaner split for backup purposes.  Main drawbacks of a data partition are (a) that it's more technically challenging to do (one has to mount the partition, then symlink folders into /home); and (b) when you upgrade the system (generally every two years) you have to redo software config settings, as those were saved in the old home folder.  OTOH, your helper shouldn't find this challenging (if so, get another one) and there's an advantage to clearing out the cobwebs every couple years.  FWIW, it's what I do, and have for many years.

I wanna switch to using the every 6 months Ubuntu and drop the LTS Ubuntu. Will what you suggest above work if I switch to new Ubuntu versions every 6 months? I definitely don't want to nuke and pave and recreate my system every 6 months. Sounds like I would have to get and pay for expert Linux help every 6 months and that's too much hassle.

Your thoughts? Thx.

---

### Post by Advait on 2023-10-19
> **MAFoElffen said:**
> But... Most of ZFS's management is command line. The only tools I know of that are GUI are the web based Scale UI (Scale Out ZFS) of TrueNAS, and BUI of Oracle ZFS Storage Manager (which is non-free and very costly). TrueNAS does say they are based on Debian. But is has no installed Desktop.

Using the command line to take and manage my snapshots is definitely not an option for me. So looks like Btrfs is my only choice. Your thoughts? Thx.

And looks like only Ubuntu and OpenSuse have Btrfs GUI options that a noob could work with. That sound right?

(Also, I'll instruct my tech support to set up the grub-btrfs tool so snapshots appear in my grub menu. That's another of my hard requirements.)

---

### Post by Advait on 2023-10-19
> **MAFoElffen said:**
> I just finished this Worksation, so not much on it yet, But a good example.
```

$ sudo zfs list
...
dpool                                           2.93M   450G       96K  /dpool
dpool/DATA                                       192K   450G       96K  none
dpool/DATA/ubuntu_2204                            96K   450G       96K  /dpool
hpool                                           2.58G   344G      192K  /home
hpool/USERDATA                                  2.58G   344G      192K  none
hpool/USERDATA/ubuntu_2204                      2.58G   344G     2.58G  /home
kpool                                            406G   493G       96K  /kpool
kpool/QEMU-KVM                                   406G   493G       96K  none
kpool/QEMU-KVM/ubuntu_2204                       406G   493G      104K  /kpool
kpool/QEMU-KVM/ubuntu_2204/ISO                   406G   493G      406G  /kpool/ISO
kpool/QEMU-KVM/ubuntu_2204/KVM-VM                 96K   493G       96K  /kpool/KVM-VM
kpool/QEMU-KVM/ubuntu_2204/images                112K   493G      112K  /var/lib/libvirt/images
kpool/QEMU-KVM/ubuntu_2204/libvirt               620K   493G      620K  /etc/libvirt/
...

$ lsblk -e7 -o name,label,mountpoint
NAME        LABEL           MOUNTPOINT
sda                         
...
&#9500;&#9472;sda2      Win_G           /home/mafoelffen/WIN_G
...

```

Cool. You passed the interview test. Can I hire you set up my new Btrfs system? :P  :D  :cool:

---

### Post by pbear42 on 2023-10-19
> **Advait said:**
> I wanna switch to using the every 6 months Ubuntu and drop the LTS Ubuntu. Will what you suggest above work if I switch to new Ubuntu versions every 6 months? I definitely don't want to nuke and pave and recreate my system every 6 months. Sounds like I would have to get and pay for expert Linux help every 6 months and that's too much hassle.

Your thoughts? Thx.
Upgrading every six months is an advanced strategy.  Expecting it to be simple isn't realistic.  ;) 

Anyhoo, was just a thought.  Good luck.

---

### Post by Advait on 2023-10-19
> **pbear42 said:**
> Upgrading every six months is an advanced strategy.  Expecting it to be simple isn't realistic.  ;) 

Could you elaborate on what you mean by "advanced strategy"? That would be helpful.

A number of years ago my setup was using 6 months Ubuntu. Every 6 months I would just click the "Upgrade" button and my system would upgrade to the new 6 months version. Is that what you mean by "advanced strategy"? Just want to make sure I have the correct understanding.

---

### Post by MAFoElffen on 2023-10-19
+1 -- Thank you pbear42... I missed that he said that. That does seem ambitious, but not a sound idea. (Sorry, jumping on my soap box.)

My upgrade strategy is for my day-to-day to be on LTS. I upgrade every two years. 

I do DEV testing. That is not my job. I volunteer. Just as I volunteer support here, I get interested in some personal projects, that I take on as a challenge. I do gaming to unwind. I go fishing a lot... and I work. I have to manage my time.

I commonly do 1-3 fresh installs daily. I have install scripts to help me with my test-cases, but a lot of it is still manually. I also keep some DEV images persistent so I can test the updates on those. I expect them to be a challenge and have problems, somewhere. Which then takes time, looking at work-around's, and reporting bugs. 

My day-to-day go-to platform should not be a challenge. It should be STABLE.

LTS version are considered as STABLE. The interim Releases are considered as rolling DEVELOPMENT releases. Expect changes, and things happening, because it is not considered as stable.

My migration strategy is that I keep track of an installation... What I have where (Data). Where the config's are that I modified (Config's & Cron schedules). What programs I manually installed (Manually installed list). Etc.

On a fresh install, I generate a post installation script, to reinstall manually installed programs and to restore configs and schedules. Then I move my data into the new installation. 

A fresh install of a new release takes about 10-15 minutes. The post installation script takes about 15-20 minutes. Moving my data back into place takes about 5 minutes. So, well under an hour, for a system that has 12-15 drives. Both my server and my main workstation have this much storage. My main laptop has 3 internal drives (5TB internal storage). I want them to be predictable.

I have still have crashed my systems doing some tweaking and had to recover. I do some crazy things sometimes to see if they will work. Sometimes they don't. LOL. I am human. But I try to "learn" from my mistakes. My configuration notes and scripts help me to recovery quickly... A good migration plan feeds into a good disaster & recovery plan.

I am a fan of having a plan.

---

### Post by #&amp;thj^% on 2023-10-19
+1 to the above.
particularity this "I am a fan of having a plan."
So far I think the Op has a few plans in mind none of which I would suggest.
A choice has to made here Avait, as to what you want as a system first.
Another way to confuse you even more :D
```
zfs list
NAME                                 USED  AVAIL     REFER  MOUNTPOINT
zroot                               10.5G   435G       96K  legacy
zroot/ROOT                          10.4G   435G       96K  legacy
zroot/ROOT/backup-2023-10-19-10-57     8K   435G     6.70G  /
zroot/ROOT/default                  10.4G   435G     7.28G  /
zroot/tmp                            148K   435G      148K  /tmp
zroot/usr                            120M   435G       96K  /usr
zroot/usr/home                       120M   435G      120M  /usr/home
zroot/usr/ports                       96K   435G       96K  /usr/ports
zroot/usr/src                         96K   435G       96K  /usr/src
zroot/var                            488K   435G       96K  /var
zroot/var/audit                       96K   435G       96K  /var/audit
zroot/var/crash                       96K   435G       96K  /var/crash
zroot/var/mail                       104K   435G      104K  /var/mail

```
Did we mention very flexible  lol
```
 zpool status
  pool: zroot
 state: ONLINE
config:

	NAME        STATE     READ WRITE CKSUM
	zroot       ONLINE       0     0     0
	  nvd0p2    ONLINE       0     0     0

errors: No known data errors

```

---

### Post by Advait on 2023-10-20
> **MAFoElffen said:**
> +1 -- Thank you pbear42... I missed that he said that. That does seem ambitious, but not a sound idea. (Sorry, jumping on my soap box.)

My upgrade strategy is for my day-to-day to be on LTS. I upgrade every two years. 

I do DEV testing. That is not my job. I volunteer. Just as I volunteer support here, I get interested in some personal projects, that I take on as a challenge. I do gaming to unwind. I go fishing a lot... and I work. I have to manage my time.

I commonly do 1-3 fresh installs daily. I have install scripts to help me with my test-cases, but a lot of it is still manually. I also keep some DEV images persistent so I can test the updates on those. I expect them to be a challenge and have problems, somewhere. Which then takes time, looking at work-around's, and reporting bugs. 

My day-to-day go-to platform should not be a challenge. It should be STABLE.

LTS version are considered as STABLE. The interim Releases are considered as rolling DEVELOPMENT releases. Expect changes, and things happening, because it is not considered as stable.

My migration strategy is that I keep track of an installation... What I have where (Data). Where the config's are that I modified (Config's & Cron schedules). What programs I manually installed (Manually installed list). Etc.

On a fresh install, I generate a post installation script, to reinstall manually installed programs and to restore configs and schedules. Then I move my data into the new installation. 

A fresh install of a new release takes about 10-15 minutes. The post installation script takes about 15-20 minutes. Moving my data back into place takes about 5 minutes. So, well under an hour, for a system that has 12-15 drives. Both my server and my main workstation have this much storage. My main laptop has 3 internal drives (5TB internal storage). I want them to be predictable.

I have still have crashed my systems doing some tweaking and had to recover. I do some crazy things sometimes to see if they will work. Sometimes they don't. LOL. I am human. But I try to "learn" from my mistakes. My configuration notes and scripts help me to recovery quickly... A good migration plan feeds into a good disaster & recovery plan.

I am a fan of having a plan.

I was just teasing about hiring you. I would like to hire you but, as you detailed, you've got other commitments.

Good info. Thanks. When I talk with the hired Linux expert, I'll ask them to advise me re trying 6 months rolling vs sticking with LTS. I'll have them read this thread to get all the details.

---

### Post by Advait on 2023-10-20
> **1fallen said:**
> +1 to the above.
particularity this "I am a fan of having a plan."
So far I think the Op has a few plans in mind none of which I would suggest.
A choice has to made here Avait, as to what you want as a system first.
Another way to confuse you even more 

Too late, I'm already confused. :P In any case, I'll hire and good Linux expert and hopefully they'll put me on the best path. I'll tell them what I want, then they'll have a good laugh and tell me what is actually best. :P

---

