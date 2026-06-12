---
title: "error mounting /dev/sdc1 external hard drive"
date: 2021-03-21
forum: General Help
---

### Post by nick2learn on 2021-03-21
Hi,
I have recently bought a 2TB seagate USB expansion drive... it used to work, VERY slowly as I started doing a back up until it eventually seemed to just keep freezing as it added more data (nowhere near capacity) Now I have an error mounting /dev/sdc at media/nick/seagate expansion drive: Unknown error when mounting /dev/sdc1

Can anyone help a noob please?

As a side note my I have a second HDD internal on my laptop which has never mounted automatically since having ubuntu installed... I have to open Files, then click on +Other Locations and then Data to get it to mount...

---

### Post by Bashing-om on 2021-03-22
nick2learn - Hello

As a place to start troubleshooting -
What is the file system on that problematic drive ?

with the USB drive plugged in:
what returns from terminal command:
```

sudo fdisk -lu

```

---------------------
> 
As a side note my I have a second HDD internal on my laptop which has never mounted automatically since having ubuntu installed... I have to open Files, then click on +Other Locations and then Data to get it to mount...

In this instance it is the file "/etc/fstab" that takes care of the auto mounting. Did you make an appropriate entry in this file ?

[INDENT]all in the process
[/INDENT]

---

### Post by ActionParsnip on 2021-03-22
What file system does it use?
When you unplug the device physically do you use the safe remove feature in the OS _before _unplugging?

---

### Post by nick2learn on 2021-03-22
Here's the return from "[COLOR=#000000][FONT=&amp]sudo fdisk -lu":[/FONT][/COLOR]

```


Disk /dev/sda: 119.25 GiB, 128035676160 bytes, 250069680 sectors
Disk model: KINGSTON RBU-SNS
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: F8753DEF-B32E-4953-A6A6-F271D84F106E


Device         Start       End   Sectors   Size Type
/dev/sda1       2048   1050623   1048576   512M EFI System
/dev/sda2    1050624 216682495 215631872 102.8G Linux filesystem
/dev/sda3  216682496 250068991  33386496  15.9G Linux swap




Disk /dev/sdb: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: HGST HTS721010A9
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: FDCE2619-8CC4-4629-B6C8-14AB9CC431FC


Device     Start        End    Sectors   Size Type
/dev/sdb1     40 1953525133 1953525094 931.5G Microsoft basic data


```

---

### Post by nick2learn on 2021-03-22
Yes I do... slim chance I didn't for some reason I guess

---

### Post by yancek on 2021-03-22
In your original post, you indicate that you are having problems mounting/accessing a 2TB drive shown as sdc/sdc1.  Your fdisk output does not show any 2TB drive nor does it show any drive sdc.  Verify that the drive is properly attached to the computer and run the command again.  If you get similar output, that's not good news.  Can you check in the BIOS to see if the drive is recognized?

---

### Post by tea for one on 2021-03-22
> **nick2learn said:**
> As a side note my I have a second HDD internal on my laptop which has never mounted automatically since having ubuntu installed... I have to open Files, then click on +Other Locations and then Data to get it to mount...

Disks (gnome-disk-utility) > Select drive (in left panel) > Select partition (under Volumes) > Click Gear Wheel (additional partition options) > Edit mount options > Click user session defaults > Mount at system start up

Any good?

---

### Post by oldfred on 2021-03-22
Please use code tags when posting terminal output or long text to preserve formatting and make easier to read.
How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)
[http://www.bbcode.org/reference.php](http://www.bbcode.org/reference.php)
If using Quick Reply then[noparse] ```
 at the beginning and 
``` at the end. [/noparse]

Also removed loop mounts which are just snaps as that is how those programs are mounted. Or this which excludes loops:
lsblk -o NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE,fsused,MODEL | egrep -v "^loop"

I have not been a fan of using disks to add entry to fstab. Its parameters usually are not very good. But you can edit those.
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.
And from TheFu:
[https://ubuntuforums.org/showthread.php?t=2420861&p=13865822#post13865822](https://ubuntuforums.org/showthread.php?t=2420861&p=13865822#post13865822)

I also use noatime if SSD or relatime if HDD for ext4 partitions. Although relatime supposed is now a default. See:
man mount

---

### Post by nick2learn on 2021-03-22
> **tea for one said:**
> Disks (gnome-disk-utility) > Select drive (in left panel) > Select partition (under Volumes) > Click Gear Wheel (additional partition options) > Edit mount options > Click user session defaults > Mount at system start up

Any good?

The "mount at system start up" was already checked.

---

### Post by nick2learn on 2021-03-22
Thanks... I get the first bit but the rest of it's way over my head.

---

### Post by tea for one on 2021-03-23
> **nick2learn said:**
> The "mount at system start up" was already checked.

Did you switch off [COLOR="#0000FF"]User Session Defaults[/COLOR]?

Have you rebooted?

---

### Post by nick2learn on 2021-03-23
> **tea for one said:**
> Did you switch off [COLOR=#0000FF]User Session Defaults[/COLOR]?

Have you rebooted?

Yes, switched user sessions defaults off, rebooted... would even allow me to mount the work around way I usually do, so I put it back to how it was and rebooted... now I can still do the manual work around to get it to mount (file, other locations, data)

---

