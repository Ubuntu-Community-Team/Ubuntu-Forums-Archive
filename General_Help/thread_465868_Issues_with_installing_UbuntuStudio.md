---
title: "Issues with installing UbuntuStudio"
date: 2007-06-06
forum: General Help
---

### Post by Joshiii-Kun on 2007-06-06
Hello there,

I'm having an issue with installing UbuntuStudio. This issue also applies when I'm installing the regular Ubuntu, by the way.
I've looked around the forum and I found someone who had a similar issue ([link]("http://ubuntuforums.org/showthread.php?t=422427&highlight=load+cd-rom+failed")), but I think he had that issue with a previous version of Wubi, as my Wubi installation doesn't have any .img files in the disks directory.
This person fixed his issue by making sure the disks were smaller than 4GB and he replaced the root.img file with a renamed home.img file so that is wasn't too small.

None if these symptoms apply to my installation though. All the files all present:
- home.virtual.disk (3GB)
- swap.virtual.disk (2GB)
- system.virtual.disk (3GB)

I made sure the disk sizes were smaller than 4GB, but alas, it still didn't work. I also defragmented the j:\wubi\ directory with JkDefrag. I have Wubi installed on the J drive because that's the only one with enough disk space on it.

The issue I'm getting is that early in the installation process, I get a red message saying it can't load installer components of the CD. Searching for the ISO seems to work, but it won't make the error message go away.
This error message seems to pop up during the formatting process of de system.virtual.disk drive.
So I pressed ALT+F4 to check the messages, I got these messages:

> 
WARNING ** : Configuring 'load-cdrom' failed with error code 1
WARNING ** : Menu item 'load-cdrom' failed


Also, there's something else that I find weird. After I boot up 'Ubuntu' from the boot menu, after a while it gets stuck. There are several messages on the screen (console mode, before the setup starts).
It gets stuck after telling me that there are no RAID drives. I first thought I needed to wait, so I left my computer on during the night, but the next morning the screen was still the same, stuck at the "no RAID drives" message.
When I then press ENTER, it seems to initiate an alternate initiation method.
These are the messages I'm getting (including some 'good' messages):

> 
...
initrd /wubi/boot/initrd
         [Linux-initrd @ 0x1f862000....
boot
Loading, please wait...
No RAID disks         <------- It gets stuck here, it continues when I press ENTER

Alternate init...
umount: Couldn't umount /sys: No such file or directory
mount: Mounting sysfs on /sys failed: Device or resource busy
Starting system log daemon: syslogd, klogd. <------ Not sure about this one, the picture I took was very blurry here.


What can I do to fix this?

These are the specs of my system:
> 
cpu: AMD 64 3200+ s939
motherboard: ASUS A8N-SLI
ram: 2048MB DDR 400MHz
video: nVidia Geforce 7900GT
harddisk 1: 250GB
harddisk 2: 120GB <---- This one has Wubi on it


I hope that's all you need to know. Thanks in advance :)

---

### Post by ago on 2007-06-06
You can try the latest minefield. [http://cutlersoftware.com/ubuntusetup/devel/minefield](http://cutlersoftware.com/ubuntusetup/devel/minefield)

Uninstall and reinstall. If you get stacked with a red screen on load cdrom press alt+f4 to see what error exactly generated that. To have the full log press alt+f2, then

nano /var/log/syslog

---

### Post by Joshiii-Kun on 2007-06-06
I would post the log file, but how do I save the log file so that I can access it in Windows? There is no logs directory in the Wubi directory.

The minefield one still hangs after the "No RAID drives" message, and after pressing enter I get the same messages:

> 
Alternate init...
umount: Couldn't umount /sys: No such file or directory
mount: Mounting sysfs on /sys failed: Device or resource busy


And at the red screen I get the same messages as well:

> 
WARNING ** : Configuring 'load-cdrom' failed with error code 1
WARNING ** : Menu item 'load-cdrom' failed


Other messages I found in the log file were things like "Unable to mount loop device", "Cannot create file system for /media/host/wubi/disks/system.virtual.disk, giving up" and "Read-only device" (I don't know if that last one is very important).

---

### Post by zappazzi on 2007-06-06
> **Joshiii-Kun said:**
> 
Alternate init...
umount: Couldn't umount /sys: No such file or directory
mount: Mounting sysfs on /sys failed: Device or resource busy

we have the same issue. No such file...etc... 

[http://ubuntuforums.org/showthread.php?t=463829](http://ubuntuforums.org/showthread.php?t=463829)
:(

---

### Post by ago on 2007-06-06
> **Joshiii-Kun said:**
> Other messages I found in the log file were things like "Unable to mount loop device", "Cannot create file system for /media/host/wubi/disks/system.virtual.disk, giving up" and "Read-only device" (I don't know if that last one is very important).

Yep those are the relevant ones. The windows folder is accessible from /media/host (but it might be read only), try to copy syslog, lupin.log and zenigata.log in there then zip them from windows and post them here. Do that only with a fresh installation. Try to see the logs for relevant messages regarding "host" and/or system.virtual.disk. The other errors are irrelevant.

---

### Post by Joshiii-Kun on 2007-06-06
Yeah, /media/host is read-only. I've tried to mount it another way (though, I'm quite the Linux newbie), using fdisk -l and the mount command, but that makes another read-only accessible disk.. So, I can't copy the logs. How can I change this?

---

### Post by ago on 2007-06-06
> **Joshiii-Kun said:**
> Yeah, /media/host is read-only. I've tried to mount it another way (though, I'm quite the Linux newbie), using fdisk -l and the mount command, but that makes another read-only accessible disk.. So, I can't copy the logs. How can I change this?

ntfs-3g insists in mounting the filesystem readonly if ntfs was not closed up cleanly or is marked as dirty. You have to make sure ntfs is clean from within windows.

---

### Post by Joshiii-Kun on 2007-06-06
Hmmm, clean? How do I make sure my hard disk is clean within Windows? I don't have to reformat it, do I?

---

### Post by ago on 2007-06-06
Do a full reboot cycle in windows and try to use use Chkdsk  & co

---

### Post by Joshiii-Kun on 2007-06-07
Bleh, I just can't get it 'clean'! :( I rebooted completely, did chkdsk, defragged, everything.
Is there another way I can transfer the files somewhere else?

---

