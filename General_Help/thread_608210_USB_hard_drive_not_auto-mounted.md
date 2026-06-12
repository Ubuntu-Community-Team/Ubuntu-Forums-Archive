---
title: "USB hard drive not auto-mounted"
date: 2007-11-09
forum: General Help
---

### Post by Endolith on 2007-11-09
I've had neverending trouble with auto-mounting of my USB hard drives (ever since I upgraded to Feisty?)  Please help me troubleshoot this, as I don't even know where to look.  I have two external Seagate USB drives.  They are currently partitioned as such:

```

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d4d776f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19455   156272256    c  W95 FAT32 (LBA)

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x920b5a63

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               6        4750    38114212+   7  HPFS/NTFS
/dev/sdc2            4751       19457   118133977+   b  W95 FAT32

```

"Square-shaped" drive:

One partition:
FAT32	149 GB	"STORAGE"

"Book-shaped" drive:

Two partitions:
NTFS	36 GB	"NTFS backup"
FAT32	113 GB	"FAT BACKUP"


The partitions are always mountable by hand, but don't automount in these circumstances:


When plugged into Inspiron laptop:
Square drive:
*STORAGE* not mounted

Book drive:
*FAT BACKUP* mounted
*NTFS backup* not mounted



When plugged into Optiplex desktop:
Square drive:
*STORAGE* not mounted

Book drive:
*FAT BACKUP* mounted
*NTFS backup* mounted


Both computers are running Gutsy, with ntfs-3g enabled for read and write, and no modifications to any of the automount stuff that I can think of.

I don't think auto-mounting of removable drives is handled by fstab, so please don't tell me to brute force it that way.

---

### Post by MikeBenza on 2007-11-09
Is [this](http://ubuntuforums.org/showthread.php?t=582045) your issue?

---

### Post by Endolith on 2007-11-09
I tried removing "usefree", re-plugging the drives, rebooting, replacing "usefree", re-plugging the drives, rebooting.  Nothing.

---

### Post by jamesr on 2007-11-12
The only comment That I can make is that I had a similar problem with Xubuntu 6.06 ie LTS version but partially solved the problem by going to 7.04 and /or 7.10. I am saying "partially resolved" see post by myself, note to self will have find out how create a link. because of this post and many others who seem to have had problems when upgrading to 7.04 and 7.10.. 

I know that this reply has not helped solve your problem but I hope that somebody from Canonical reads these posts, because the drivers seem to be very finicky. I had to built up a seperate system to test out the problem because I did not want to take the risk of screwing up my archival / intranet server .

As an aside, Microsoft I believe is also having problems with Vista and PCI USB cards. I have a business aquanitance who owns a retail PC store and he was saying that some of multiple USB ported  PCI cards that worked in XP fully, only partially work in Vista. 3 out of the 5 ports work whereas the other do not. The same problem exists in Xubuntu 6.06, only 3 work.

---

### Post by Endolith on 2007-11-16
I doubt it has anything to do with drivers, since it can be mounted manually.  I will try this tomorrow: [https://wiki.ubuntu.com/DebuggingRemovableDevices](https://wiki.ubuntu.com/DebuggingRemovableDevices)

---

### Post by Tanker Bob on 2007-11-17
If you are using Kubuntu 7.10, you can simply use Dolphin's Storage Media tab, then open the stick. It will mount when you try to open it in Dolphin.

---

### Post by Endolith on 2007-11-17
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/163386](https://bugs.launchpad.net/ubuntu/+bug/163386) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **Tanker Bob said:**
> If you are using Kubuntu 7.10, you can simply use Dolphin's Storage Media tab, then open the stick. It will mount when you try to open it in Dolphin.

I am using regular GNOME Ubuntu.

---

### Post by Tanker Bob on 2007-11-17
I haven't used gnome in about a year, but you may be able to install dolphin in gnome. I have some gnome apps installed in kde. They install their support libs and work fine.

---

### Post by Endolith on 2007-11-17
> **Tanker Bob said:**
> I haven't used gnome in about a year, but you may be able to install dolphin in gnome. I have some gnome apps installed in kde. They install their support libs and work fine.

I'm sure I can, but I don't want Dolphin.  :-)  I want all of my partitions to auto-mount in GNOME.

---

### Post by Bloch on 2007-11-17
My external hard drive also fails to automount. 
When I enter ```
sudo fdisk -l
```  it appears as 
/dev/sdb1

I installed a utility called pmount and now I type

```
pmount /dev/sdb1 external
```
at the command line to mount the harddrive at the location
/media/external

In fact I use a small bash script:
```
pmount /dev/sdb1 external
sleep 2
nautilus /media/external
```

Here is the description of pmount:
> [QUOTE]pmount - mount arbitrary hotpluggable devices as normal user
pmount  ("policy mount") is a wrapper around the standard mount program
       which permits normal users to mount removable devices without a  match&#8208;
       ing /etc/fstab entry.[/QUOTE]


Come to think of it, this caused me a lot of problems at the time. Why doesn't the damn thing automount?

---

### Post by Endolith on 2007-11-17
> **Bloch said:**
> I installed a utility called pmount and now I type

Yes, I've been using pmount since it stopped working months ago.

> Come to think of it, this caused me a lot of problems at the time. Why doesn't the damn thing automount?

:-)

Follow the directions on [http://wiki.ubuntu.com/DebuggingRemovableDevices](http://wiki.ubuntu.com/DebuggingRemovableDevices) and file a bug report.

---

### Post by Endolith on 2007-11-30
Man, why is this so difficult?  It's been broken since April.  I've posted a question on Launchpad, on the forums, I've posted in other people's forum topics, and filed a bug, and still no help.

If I knew how the automounting worked I would dig around and try to find troubleshooting information myself, but I don't even know where to look or what to search for.  I can't help myself and I can't get help from anyone else.  Open source at its finest.  :-(

---

### Post by PhilRichards on 2007-12-01
**This post could be related to an Ubuntu bug filed at**: 147807 [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				udev currently can't cope with VFAT partitions with sector sizes >= 8192 (big external disks with a single VFAT partition will end up being unmountable).

---

### Post by Endolith on 2007-12-01
> **PhilRichards said:**
> **This post could be related to an Ubuntu bug filed at**: 147807 [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				udev currently can't cope with VFAT partitions with sector sizes >= 8192 (big external disks with a single VFAT partition will end up being unmountable).

I can mount it and use it fine; it just doesn't auto-mount.

There's also the NTFS partition that automounts on one computer but not the other, so it's not a problem with FAT (unless there are two separate problems).

How can I confirm whether the sector size is the problem?  When will it be fixed?

---

### Post by Endolith on 2008-04-25
Still a problem in Hardy Heron.  This time it displays an error, though: "Invalid mount option when attempting to mount the volume".

I ran fsck on one of the partitions, and it said 
```

There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  71:53/44, 72:45/53, 73:41/4b, 74:47/32, 75:41/5f, 76:54/56, 77:45/4f
  , 78:00/4c, 79:00/31
1) Copy original to backup
2) Copy backup to original
3) No action
? 3
No FSINFO sector
1) Create one
2) Do without FSINFO
? 2

```

Would this be part of the problem?  I don't boot off these partitions, so I think the boot sector is irrelevant.

....

Oh!  The boot sector difference is hex for "SEAGATE" and "DSK2_VOL1".  Would that have anything to do with it?

---

### Post by Endolith on 2008-04-25
Aha!  I ran Windows file system checks and then ran fsck on all the partitions (including adding the FSINFO sector and making the labels consistent), and now both show up as "black drives" in Computer and both give the "Invalid mount option when attempting to mount the volume" error (which did not happen before).  There is also another error now:

> DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Both mount just fine if I use pmount, but won't auto-mount.

---

### Post by Endolith on 2008-04-27
Tried re-installing hal as in this thread: [http://ubuntuforums.org/showthread.php?t=571768](http://ubuntuforums.org/showthread.php?t=571768)

but still no luck.

Other similar threads:

[http://ubuntuforums.org/showthread.php?t=503703](http://ubuntuforums.org/showthread.php?t=503703) (commenting out a line in fstab fixed it)
[http://ubuntuforums.org/showthread.php?t=766719](http://ubuntuforums.org/showthread.php?t=766719) 
[http://ubuntuforums.org/showthread.php?t=731223](http://ubuntuforums.org/showthread.php?t=731223)

---

### Post by Bloch on 2008-04-29
Does this solution help:

Some users report that flash memory devices fail to automount after the upgrade (not fresh installation) to 8.04 Hardy Heron

The issue relates to this bug in Gutsy: [https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025)


Here is a solution:

Open from menu:    Applications > System Tools > Configuration Editor

Go to the key 
system > storage > default_options > vfat
Edit the ```
mount_options
``` key (double click it) and remove the ```
usefree
``` option.

You may need to reboot.
The devices should then automount when plugged in: i.e. the icon will appear on the desktop.

I emailed one of the developers involved, Martin Pitt.
> That's indeed the right solution. 'usefree' is deprecated in Hardy (it
was only a temporary hack in Gutsy), and thus the gnome-mount
option 'usefree' has been removed in Hardy again.

You need it in Gutsy to avoid minute-long hangs when mounting a VFAT
drive. In Hardy this was fixed properly in the kernel.

If this key does not exist then clearly this solution does not apply to your problem.

---

### Post by Endolith on 2008-04-29
> **Bloch said:**
> Go to the key 
system > storage > default_options > vfat
Edit the ```
mount_options
``` key (double click it) and remove the ```
usefree
``` option.


Tried that in November: [http://ubuntuforums.org/showthread.php?t=608210#3](http://ubuntuforums.org/showthread.php?t=608210#3)

But it didn't help.  Maybe I will try again.

---

### Post by Endolith on 2008-04-30
> **Bloch said:**
> Applications > System Tools > Configuration Editor

Doesn't exist, but I ran gconf-editor.

> If this key does not exist then clearly this solution does not apply to your problem.

It did still exist, and I removed it.  And the drives showed up after rebooting!  This did not happen last time I removed the key, so I put the key back in.  Maybe this was a combination of the FAT headers being screwed up (fsck) and the usefree key.  I THINK YOU FIXED MY PROBLEM!

---

### Post by Yellowbelly on 2008-05-01
I'm having this exact problem with 2 fat 32 partitions not automounting but usefree isn't in the conf editor :(... Any help?

---

### Post by Endolith on 2008-05-01
> **Yellowbelly said:**
> I'm having this exact problem with 2 fat 32 partitions not automounting but usefree isn't in the conf editor :(... Any help?

Can you mount them manually?  Have you fun fsck or dosfsck to test them?

---

### Post by prateekv on 2008-05-01
I have a seagate external drive 100 GB and its not working when I plug it in thru USB. Please tell me what to do. I am a beginner in Ubuntu.

---

### Post by Endolith on 2008-05-01
> **prateekv said:**
> I have a seagate external drive 100 GB and its not working when I plug it in thru USB. Please tell me what to do. I am a beginner in Ubuntu.

If you go to Places --> Computer, does it show up?  Maybe with a different icon?

Can you mount it manually by typing "pmount /dev/sda1" at the command line?  You need to know which location it's in, though.  /dev/sda1, /dev/sdb2, etc.

---

### Post by Yellowbelly on 2008-05-01
It shows up under places but not the desktop. Rhythmbox won't recognize my music stash until I click on it which I assumes mounts it. It's recognized but not automounted I guess. I don't have to manually mount it every time so it's not a huge hassle, just a minor one that I don't wanna deal with anymore.

I just got done renaming the partitions too so if I fix this, i'll be good to go with this new release.

---

### Post by Endolith on 2008-05-01
> **Yellowbelly said:**
> It shows up under places

With a different style icon until after you click on it?

Have you run fsck?  Can you run a detailed disk check in Windows on these partitions?  fsck complained that my disk label and the "backup" disk label stored in the file system didn't match.  I'm not sure if this was what prevented it from automounting or if the FSINFO thing prevented it.

---

### Post by Yellowbelly on 2008-05-01
no same icon and everything. It used to be called by the size of the partition until I changed that with mtools so I renamed them. That worked but it still won't automount.

I don't know how to run fsck. These drives are fine under windows and previous ubuntus.

---

### Post by Endolith on 2008-05-01
> **Yellowbelly said:**
> no same icon and everything.

On my theme, the unmounted drives had a dark colored top until I right-clicked and mounted them.

> I don't know how to run fsck. These drives are fine under windows and previous ubuntus.

Did you actually run the disk check though, that fixes file system errors?

Hmmm...  I think I ran something like ```
dosfsck -r /dev/sda1
```  It will then ask you for each change before it does it.

---

### Post by prateekv on 2008-05-02
Sir
I am a beginner and just installed Ubuntu yesterdy and am fascinated by it....
No it does not show up under PLaces - Computer.
Can u tell me how do i find out whats the location of the drive? (say sda1, sdb2)

Thanks
Prateek

---

### Post by prateekv on 2008-05-02
Well, I tried on my own - and tried SDB1 and it worked! It was mounted........
Thanks a lot to all.
Do i have to put this command everytime i want to run my drive? Isn't there some other way?
Thanks

---

### Post by Endolith on 2008-05-02
> **prateekv said:**
> Sir
Can u tell me how do i find out whats the location of the drive? (say sda1, sdb2)

I don't know, actually.  I'm sure there's a way to list them, but, like any command line hack, it's not very discoverable.  I usually go to /dev/disk/by-* and try to figure it out from there.  So for instance:

```
ls /dev/disk/by-uuid/
ls /dev/disk/by-path/
ls /dev/disk/by-label/
ls /dev/disk/by-id/
```

> **prateekv said:**
> Well, I tried on my own - and tried SDB1 and it worked! It was mounted........

Good!  Note that it might change each time you reboot or unplug and re-plug.  I'm not sure if there's any consistency to the path that it uses.  

> Do i have to put this command everytime i want to run my drive? Isn't there some other way?

1. It should mount itself automatically when you log in.  The fact that it's not auto-mounting means that something is broken, like my problems with usefree and FSINFO.
2. If you want to "brute force" it to mount every time the computer starts up, the standard response you'll get is to edit /etc/fstab.  I don't know if there's an easier way.

---

### Post by Yellowbelly on 2008-05-02
> **Endolith said:**
> On my theme, the unmounted drives had a dark colored top until I right-clicked and mounted them.



Did you actually run the disk check though, that fixes file system errors?

Hmmm...  I think I ran something like ```
dosfsck -r /dev/sda1
```  It will then ask you for each change before it does it.

I ran that and it said that it had differences "between boot sector and its backup." I had 3 choices: Copy original to back up, copy backup to orginal or nothing. I didn't know what the first two were so I did nothing.

---

### Post by Endolith on 2008-05-02
> **Yellowbelly said:**
> I ran that and it said that it had differences "between boot sector and its backup." I had 3 choices: Copy original to back up, copy backup to orginal or nothing. I didn't know what the first two were so I did nothing.

I got that too.  In my case, it was just that the label of the disk had been changed.  [http://ubuntuforums.org/showthread.php?p=4787111#15](http://ubuntuforums.org/showthread.php?p=4787111#15)

I selected "copy original to backup" because I wanted to keep the current label.

You can copy the hex into a hex decoder and see what it says.  It's probably just the label.  I'm not sure if this prevents it from automounting, though.  I assumed the problem was the FSINFO sector.

---

### Post by Endolith on 2008-05-02
Actually, it appears that the FSINFO and usefree solutions are related to each other:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/133567/comments/53](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/133567/comments/53)

> VFAT MOUNT OPTIONS
(...)
usefree -- Use the "free clusters" value stored on FSINFO. It'll
be used to determine number of free clusters without
scanning disk. But it's not used by default, because
recent Windows don't update it correctly in some
case. If you are sure the "free clusters" on FSINFO is
correct, by this option you can avoid scanning disk.

---

### Post by prateekv on 2008-05-02
1. It should mount itself automatically when you log in.  The fact that it's not auto-mounting means that something is broken, like my problems with usefree and FSINFO.
2. If you want to "brute force" it to mount every time the computer starts up, the standard response you'll get is to edit /etc/fstab.  I don't know if there's an easier way.[/QUOTE]

There is an easier way to automount....I got this thru a little help from my friend. 
By going to System-Preferences-Sessions, I can put the 
pmount /dev/sdb1 (whatever disk number it is) and thus whenever the PC boots, the drive shall run automatically.

We must remember that this shall work only if we plug in the drive before booting.

Prateek

---

### Post by Endolith on 2008-05-02
> **prateekv said:**
> By going to System-Preferences-Sessions, I can put the 
pmount /dev/sdb1 (whatever disk number it is) and thus whenever the PC boots, the drive shall run automatically.

That's a good alternative.  Remember that that will only work when you log in, though, not at boot.

---

### Post by prateekv on 2008-05-02
Yes, so it serves my purpose because i need the drive only when i log in.
Either way it runs automatically in Windows.
Anyways, cud u tell me how can i automate the process of mounting this drive forever?
A step by step explanation wud be better.

Thanks

---

### Post by Endolith on 2008-05-02
> **prateekv said:**
> Anyways, cud u tell me how can i automate the process of mounting this drive forever?
A step by step explanation wud be better.

I'm not good with fstab:

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://en.wikipedia.org/wiki/Fstab](http://en.wikipedia.org/wiki/Fstab)

---

### Post by prateekv on 2008-05-03
Okay Thanks i will read that.

---

