---
title: "Error: mount: can't find /dev/sdb in /etc/fstab.....after attaching external USB HDD."
date: 2013-11-25
forum: General Help
---

### Post by patriot56 on 2013-11-25
Greetings forum.

I am posting here for this issue because I couldn't find another area that I thought was appropriate.

I have a 1 TB. USB HDD (a WD My Book) that I am trying to use on a Linux Lite (Ubuntu 12.04 LTS) computer and when I try to mount the drive from the Terminal using  ```
mount
``` command I get the error, **mount: can't find /dev/sdb in /etc/fstab**.

I can see the drive icon on my Desktop and I can '[COLOR=#0000ff]right click[/COLOR]' or "[COLOR=#0000ff]Double Click[/COLOR]" the icon and open the drive however, I cannot add anything to the drive.  I cannot drag-and-drop any files to the drive and the options to '[COLOR=#0000ff]Create Folder[/COLOR]' and '[COLOR=#0000ff]Create Document[/COLOR]' are greyed out. (As are several other actions)

I'm assuming that this is a permissions thing but I haven't been able to find a solution.

I need to be able to move this drive from computer to computer with **Windows** on some and **Linux** on others, and be able to just plug it into a USB port and have it automatically mounted and fully accessable to any user.  Just as if it were a *Flash Drive* being inserted.

Is there a way to do this?  I would like to partition the drive into 100 MB slices.

Thank you in advance for any help provided.

patriot2135

---

### Post by ajgreeny on 2013-11-25
What is the filesystem on the external drive and exactly what command are you using to mount it?

Can we also see your /etc/fstab file.

---

### Post by patriot56 on 2013-11-25
> **ajgreeny said:**
> What is the filesystem on the external drive and exactly what command are you using to mount it?

Can we also see your /etc/fstab file.

In an attempt to mount the drive I have tried the following:

```
mount /dev/sdb
mount /dev/sdb1
sudo mount /dev/sdb
sudo mount /dev/sdb1 /mnt 
```

Though I have included each of these commands in the same code wrap here; in reality, I entered each code seperatly in the Terminal.

As requested, here is a copy of my **/etc/fstab** file:

> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a3f7729b-2d0b-4d9d-be84-14ee3ead0e02 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=942641a9-71c4-4ba2-880e-6dc1ddb7c18d none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


Also, if this is helpful, I have run the following command in Terminal:
```
sudo blkid
```
With the following results:
> /dev/sda1: LABEL="Linux Lite" UUID="a3f7729b-2d0b-4d9d-be84-14ee3ead0e02" TYPE="ext4" 
/dev/sda3: LABEL="SliTaz" UUID="afa27140-15d9-49ad-beb1-a13e87a0d0e6" TYPE="ext4" 
/dev/sda5: UUID="942641a9-71c4-4ba2-880e-6dc1ddb7c18d" TYPE="swap" 
/dev/zram0: UUID="df3dc735-1ac7-44a3-a40b-50668702847b" TYPE="swap" 
/dev/sdb1: UUID="f36c7528-f873-44ea-8b4d-b14e6a8089ed" TYPE="ext4" 

The last item in the list corresponds to the line of numbers that **[COLOR=#0000ff]Ubuntu Disk Utility 3.0.2[/COLOR]** provides under Mount Point : [COLOR=#0000ff]Mounted at[/COLOR] /media/f36c7528-f873-44ea-8b4d-b14e6a8089ed

Thank you for responding.

I hope the information I have provided helps.
Please let me know if I can help further.

Respectfully,

patriot2135

---

### Post by steeldriver on 2013-11-25
If you can see the drive in /media and can open and browse it from the file manager then it *is* already mounted - if you can't write to / create folders on it, that's a different thing. Typing

```
mount | grep media
```

should show you what options it was mounted with, and

```
ls -l /media
```

should show you the current ownership and permissions - usually removable media should get auto-mounted with the ownership of the current desktop user (allowing them read-write access) but things can go wrong - for example if the filesystem is not 'clean' and gets mounted read-only.

---

### Post by patriot56 on 2013-11-25
> **steeldriver said:**
> If you can see the drive in /media and can open and browse it from the file manager then it *is* already mounted - if you can't write to / create folders on it, that's a different thing.
In every way that I can imagine, that makes perfect sense and I have *thought that* all along.  However, I am still learning how everything works in Linux so I don't take anything for granted.

> **steeldriver said:**
> 
 Typing

```
mount | grep media
```

should show you what options it was mounted with, and

```
ls -l /media
```

should show you the current ownership and permissions - usually removable media should get auto-mounted with the ownership of the current desktop user (allowing them read-write access) but things can go wrong - for example if the filesystem is not 'clean' and gets mounted read-only.

The commands above did exactly as you stated, and much to my supprise, I actually understood a lot of it, however if I need to change the permissions of the drive/partition each time the device is pluggen into a different computer it won't work for the job that I hope to use it for.

_**Question**_: What if I format the entire drive and re-partition it in the 100MB slices like I entend to do?  Could that possibly solve this issue?

Awaiting a response before attempting any further action.

Thank you.  I appreciate your help and advice.

patriot2135

---

### Post by steeldriver on 2013-11-25
The partitioning shouldn't matter I don't think (why exactly do you want to do that btw? also, if it's an MBR partition table you may have issues creating that many partitions)

What *should* happen by default is that the udisks daemon notices when you plug in a USB device and mounts it with you as the owner, with rw permissions. If you open a terminal and run 'udisks --monitor' and then plug the drive in you should see something like this:

```

steeldriver@lap-t61p:~$ udisks --monitor
Monitoring activity from the disks daemon. Press Ctrl+C to cancel.
added:     /org/freedesktop/UDisks/devices/sdb
added:     /org/freedesktop/UDisks/devices/sdb1
job-changed: /org/freedesktop/UDisks/devices/sdb1
changed:     /org/freedesktop/UDisks/devices/sdb1
job-changed: /org/freedesktop/UDisks/devices/sdb1
^C

```
after which checking the /media directory shows

```

steeldriver@lap-t61p:~$ ls -l /media
total 8
drwx------ 1 steeldriver steeldriver 4096 Jun 24 15:19 Seagate Expansion Drive

```

allowing you (as owner) to write to it - what do you see?

---

### Post by patriot56 on 2013-11-25
> **steeldriver said:**
> The partitioning shouldn't matter I don't  think (why exactly do you want to do that btw? also, if it's an MBR  partition table you may have issues creating that many  partitions)

_**Short answer?**_  *(And at the risk of potentially "derailing" this thread)....* I want to load the drive with Movies, Videos, Music, etc., and share it on a LAN. **Eventually**!!!--- **Maybe**!!!---

Currently, this drive is attached to *my* computer, where it will  be loaded with the files that I mentioned.   After that I hope to add it  to a different computer that will share it on a LAN.  Inherentally,  making it a "Media Library" share. Of sorts.

> **steeldriver said:**
> What *should* happen by default is that the  udisks daemon notices when you plug in a USB device and mounts it with  you as the owner, with rw permissions. If you open a terminal and run  'udisks --monitor' and then plug the drive in you should see something  like this:

```

steeldriver@lap-t61p:~$ udisks --monitor
Monitoring activity from the disks daemon. Press Ctrl+C to cancel.
added:     /org/freedesktop/UDisks/devices/sdb
added:     /org/freedesktop/UDisks/devices/sdb1
job-changed: /org/freedesktop/UDisks/devices/sdb1
changed:     /org/freedesktop/UDisks/devices/sdb1
job-changed: /org/freedesktop/UDisks/devices/sdb1
^C

```
after which checking the /media directory shows

```

steeldriver@lap-t61p:~$ ls -l /media
total 8
drwx------ 1 steeldriver steeldriver 4096 Jun 24 15:19 Seagate Expansion Drive

```

allowing you (as owner) to write to it - what do you see?

I issued the ```
'udisks --monitor'
``` command, then unplugged the  drive.  I then waited a couple of seconds and plugged the drive in  again, and this is the output I received:

> jaaj@stargate1:~$ udisks --monitor
Monitoring activity from the disks daemon. Press Ctrl+C to cancel.
removed:   /org/freedesktop/UDisks/devices/sdb1
removed:   /org/freedesktop/UDisks/devices/sdb
added:     /org/freedesktop/UDisks/devices/sdb
added:     /org/freedesktop/UDisks/devices/sdb1
job-changed: /org/freedesktop/UDisks/devices/sdb1
changed:     /org/freedesktop/UDisks/devices/sdb1
job-changed: /org/freedesktop/UDisks/devices/sdb1
changed:     /org/freedesktop/UDisks/devices/sdb

> **steeldriver said:**
> ....after which checking the /media directory shows

```

steeldriver@lap-t61p:~$ ls -l /media
total 8
drwx------ 1 steeldriver steeldriver 4096 Jun 24 15:19 Seagate Expansion Drive

```

allowing you (as owner) to write to it - what do you see?

I checked the /media directory as you suggested and this is the output:

> aaj@stargate1:~$ ls -l /media
total 20
drwxr-xr-x 2 root root 4096 Nov 25 08:40 1TB-HDD
drwxr-x--- 2 root root 4096 Aug  1 07:40 apt
drwxr-xr-x 2 root root 4096 Jun 21 08:12 cdrom
drwxr-xr-x 3 root root 4096 Nov 23 23:39 f36c7528-f873-44ea-8b4d-b14e6a8089ed
lrwxrwxrwx 1 root root    7 Jul 30 20:16 floppy -> floppy0
drwxr-xr-x 2 root root 4096 Jul 30 20:16 floppy0


Please believe me when I say that, I really appreciate your help so far.
I have learned more in this short "conversation" than in several days of searching for a solution for this matter.

Gratefully,
patriot2135

---

### Post by patriot56 on 2013-11-26
Solved this problem by following the instructions in the following two links:
[LIST=1]
[*] [https://www.linuxliteos.com/manual/install.html#ext4](https://www.linuxliteos.com/manual/install.html#ext4)
[*][https://www.linuxdistrocommunity.com/forums/showthread.php?tid=1465&pid=9874#pid9874](https://www.linuxdistrocommunity.com/forums/showthread.php?tid=1465&pid=9874#pid9874)
[/LIST]

These instructions work for Linux Lite but since LL is built on Ubuntu 12.04 LTS I would assume that they should work for most, if not all, Ubuntu distro.'s.  I haven't confirmed this though so, use these instructions with a measure of common sense.  If you aren't sure, ask someone.

I hope this helps with anyone else that is having the same problem

Cheers.

patriot2135

---

### Post by ajgreeny on 2013-11-26
/dev/sdb1: UUID="f36c7528-f873-44ea-8b4d-b14e6a8089ed" TYPE="ext4"                      

Is that your USB disk?

If so it is the **ext4** filesystem that is your main problem, as the mountpoint it makes when you insert it will not be owned by the user by default.  If it is the disk in question is there a good reason why it has to be ext4 and not ntfs which will I believe be mounted and usable by users in most versions of linux (those with ntfs-3g installed, I think) with no further action needed.  I have no free disks I can format to ntfs to use to test this, I'm afraid, so await other answers before jumping to re-format the disk.

EDIT:
I've just seen your post 8 in the thread which shows that the ext4 filesystem was indeed your problem, and that now you feel you have it all sorted.

---

