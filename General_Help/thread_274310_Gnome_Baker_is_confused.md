---
title: "Gnome Baker is confused"
date: 2006-10-09
forum: General Help
---

### Post by puppy on 2006-10-09
Hi folks - I'm trying to use GnomeBaker to burn DVDs but am having problems

Gnomebaker keeps insisting that I put discs into my DVD-ROM drive, even though both my drives are listed under Preferences >>> Devices

The only thing I can think is that only the DVD-ROM drive displays a mount point, the DVD-RW drive has a blank entry.

Can anyone offer any advice on what I can do to get it working??

---

### Post by Darrious on 2006-10-09
I'll usually make sure first that the dvd drives are both mounted to the computer properly. I mean as in opening your computer up then making sure that all of the connections are in ALL THE WAY. I would push the cord in anyway, just to make sure. If that does not help then I would try to see if just one works. Sometimes it can confuse the computer if there are two. Check to see which one is master and which one is slave.

If it still does not work for you, then I would do ```
sudo mount /dev/dvdrw/
``` Or whatever the device is located in.

Then I would try ```
sudo umount /dev/dvdrw/
```And remount it ```
sudo mount /dev/dvdrw/
```

---

### Post by puppy on 2006-10-09
I think we're getting there - 

after issuing the command: sudo mount /dev/dvdrw/

I get the following:

mount: can't find /dev/hda in /etc/fstab or /etc/mtab

What next?

---

### Post by jocko on 2006-10-09
I had a similar problem. It was caused by bad gconf settings.
Check which devices your dvd-rom and dvd-rw are (start **hal-device-manager**, find the dvd:s, check the "advanced" tab and see what the first line says for both devices (something like /dev/hdx or perhaps /dev/sdx)).
I my case I have a DVD-rom (/dev/hdb) and a DVD-rw (/dev/hda).
Next check which mount points these devices have (check the output of '**cat /etc/fstab**'). The relevant parts of my output is this:
```
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0
```According to this my DVD-rom is /dev/hdb and is mounted in /media/cdrom0 and my DVD-ram is /dev/hda and is mounted i /media/cdrom1

Next, start **gconf-editor**, browse the tree to apps/GnomeBaker/Devices. Here I have two entries; Device01 and Device02. Check that the keys (DeviceId, DeviceNode and MountPoint) have the correct values (I guess you can figure out which device is which from the DeviceName keys).
In my case my DVD-rom was erroneously set to /dev/hda and my DVD-rw to /dev/hdb.
To get gnomebaker to work I had to change the DeviceId and DeviceNode keys for Device01 into /dev/hdb and for Device02 into /dev/hda.

Hope this helps!

---

### Post by puppy on 2006-10-09
OK now I'm confused

in hal-device-manager, the DVD-RW drive is listed as /dev/hda and it's "storage.policy.desired_mount_point" is "dvdrecorder"

The drive is *not* listed under /etc/fstab at all

However the device is listed with the correct "DeviceID" in Gconf Editor >>> GnomeBaker >>> Devices >>> Device02  i.e. /dev/hda but has no mount point listed...

Any advice?

---

### Post by Darrious on 2006-10-09
> 
in hal-device-manager, the DVD-RW drive is listed as /dev/hda and it's "storage.policy.desired_mount_point" is "dvdrecorder"

This is the same for me, and my drive works fine, so I would not worry about that. I could be wrong though.

>  The drive is *not* listed under /etc/fstab at all

This one I'm not to sure about. I remember reading somewhere that you might need to add this device and mount point in  /etc/fstab. 

> However the device is listed with the correct "DeviceID" in Gconf Editor >>> GnomeBaker >>> Devices >>> Device02 i.e. /dev/hda but has no mount point listed...


I do not have GnomeBaker so I would not know. When I run gconf-editor I go to apps -> gnome-cd  and my device is listed there.

Well, that's my advice.

---

### Post by jocko on 2006-10-09
> **puppy said:**
> OK now I'm confused

in hal-device-manager, the DVD-RW drive is listed as /dev/hda and it's "storage.policy.desired_mount_point" is "dvdrecorder"

The drive is *not* listed under /etc/fstab at all

However the device is listed with the correct "DeviceID" in Gconf Editor >>> GnomeBaker >>> Devices >>> Device02  i.e. /dev/hda but has no mount point listed...

Any advice?

I think you have to add it to /etc/fstab.```

sudo gedit /etc/fstab
```
add this to the end:
```
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0
``` (first check that nothing else should get mounted as /media/cdrom1. Also make sure the directory /media/cdrom1 exists (otherwise run 'sudo mkdir /media/cdrom1'))
Then add the correct mount point (/media/cdrom1) to gconf-editor/apps/GnomeBaker/Devices/Device02

---

### Post by puppy on 2006-10-10
Thanks for the advice Jocko and all but this is a known bug in the current (0.6.0) version of GnomeBaker :-#

---

### Post by jocko on 2006-10-12
> **puppy said:**
> Thanks for the advice Jocko and all but this is a known bug in the current (0.6.0) version of GnomeBaker :-#

Well, I'm running GnomeBaker 0.6.0 without any problems since I fixed it. I haven't found anywhere that it's a known bug. Did you manage to solve it?

---

### Post by puppy on 2006-10-13
Unfortunately not - I'm running K3B instead :)

---

