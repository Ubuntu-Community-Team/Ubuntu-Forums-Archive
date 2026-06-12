---
title: "No mount rights for usb drive"
date: 2008-03-29
forum: General Help
---

### Post by bogdanbiv on 2008-03-29
I have Kubuntu 7.10.
I cannot mount my usb flash any more:
when pluging a flash drive in the usb port a popup comes up saying `Unmounted removable medium`. It has 2 actions availabe "Open in a new window." and "Do nothing". If I choose open a new window a Konqueror windows opens and shows a pop-up saying "Permissions denied".

How can I repair it?

---

### Post by dstew on 2008-03-29
Plug in the drive, and select "Open in a new window" Close the window. Open a terminal window and enter```
cat /etc/mtab
```Post the result to the forum.

---

### Post by bogdanbiv on 2008-03-30
Hello,
here's the output:

```
zbog@bogdan-duo:~$ cat /etc/mtab
/dev/sda2 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
/dev/sda3 /home ext3 rw 0 0
/dev/sda1 /media/sda1 fuseblk rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=512 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
```

In the address bar of the konqueror window I see "system:/media/sdb1".

Also I configured the "Open in new window" as a default action, so it now attempts to mount it and display its contents automatically, without showing any popup. (How do I undo that?)

---

### Post by bogdanbiv on 2008-03-30
UPDATE:
I noticed the message has changed to no mount point. So I did:

```
zbog@bogdan-duo:~$ sudo mkdir /media/CORSAIR
[sudo] password for zbog:
zbog@bogdan-duo:~$ ls /media
cdrom  cdrom0  CORSAIR  floppy  floppy0  sda1
zbog@bogdan-duo:~$

```

And it works! I can read/write to disk. However I don't remember deleting any /media/CORSAIR directory.

Several issues remain that I would like to understand better:

1) There is still the small issue with opening a new window by default (not showing any pop-ups). Where do I change that?
Can I choose different default actions to be performed by default on automount (ie, for user A just open a window, "don't bother me with a popup with options", user B is a power user and likes to choose different actions from the popup)?

2) Here is the output of 'cat /etc/mtab now:
```
/dev/sdb1 /media/CORSAIR vfat rw,noexec,nosuid,nodev 0 0
/dev/sdc1 /media/CORSAIR-1 vfat rw,nosuid,nodev,noatime,flush,uid=1000,utf8,shortname=lower 0 0
```
But I have only one flash drive named "CORSAIR"! How come, can someone explain?

3) In the Disk & Filesystem there is a pop-up that appears when choosing `Modify`, 
how can I learn what mean the following terms: 
"device
 * by name ________, 
 * by uuid   ________, 
 * by label  ________."

I suppose 'Enable at start-up' has something to do with automount. Can you give more details on that?

---

### Post by ante.wessels on 2008-03-30
> **bogdanbiv said:**
> 

2) Here is the output of 'cat /etc/mtab now:
```
/dev/sdb1 /media/CORSAIR vfat rw,noexec,nosuid,nodev 0 0
/dev/sdc1 /media/CORSAIR-1 vfat rw,nosuid,nodev,noatime,flush,uid=1000,utf8,shortname=lower 0 0
```
But I have only one flash drive named "CORSAIR"! How come, can someone explain?

Are you sure you wrote to the external disk? If you just make a directory, but do not mount the drive to that, the data gets written to the local disk.

---

### Post by fsmithred on 2008-03-30
> **bogdanbiv said:**
> 
I1) There is still the small issue with opening a new window by default (not showing any pop-ups). Where do I change that?
Can I choose different default actions to be performed by default on automount (ie, for user A just open a window, "don't bother me with a popup with options", user B is a power user and likes to choose different actions from the popup)?


I don't know where it is in the menu, but find kde control center ('kcontrol' in a terminal will get you there if you can't find it) and go to Peripherals --> Storage Media. Then go to the drop-down and select Unmounted Removable Media. Messing with that should get you what you want, or you can set it back to the default behavior.

---

### Post by dstew on 2008-03-30
What happens with USB devices is that the udev program attempts to mount them automatically according to its own rules. When udev mounts the device, it creates a mount point folder in /media with the name being the same as the volume ID of the device. When the device is unplugged, the directory goes away. In order to change permissions on a USB device, you have to chmod the mount point folder when the drive is plugged in and mounted, and then (I think) this information is stored, and the next time it is mounted udev puts on the mount point the permissions it last had. If you create a mount point with the name of the device, I think udev will not use that mount point, but creates a new mount point with a name like CORSAIR-1. The only way to get udev to use the mount point you created is to put an entry into /etc/fstab. And, if you make an fstab entry, use as the device name LABEL=CORSAIR instead of /dev/sdb or whatever. Then, the mount point will be specific for that USB stick. See [this excellent blog post]("http://blog.linuxoss.com/2006/10/07/suse-automatically-mount-usb-hard-drives/").

But, if you just want to update the permissions of the USB drive, let udev mount it, and chmod the permissions of the mount point. You can chown also. but it should mount as owned by the current user. If you once mounted it when you were root (hope you didn't activate the root account) it might be owned by root at every mount, so you don't have permissions. Anyway, just check the permissions and owner with```
ls -1 /media
```when the drive is mounted, and you will see what you need to do.

---

### Post by bogdanbiv on 2008-03-30
@ante.wessels:
> **ante.wessels said:**
> Are you sure you wrote to the external disk? If you just make a directory, but do not mount the drive to that, the data gets written to the local disk.

I opened a file on the flash drive and edited it, unplugged the device, and remount it.
after removing it checked the contents of /media/CORSAIR. Well, it's empty.

More than that if I try to write to it, it says permission denied.
```

zbog@bogdan-duo:~$sudo touch /media/CORSAIR/sds
touch: cannot touch `/media/CORSAIR/sds': Input/output error
zbog@bogdan-duo:~$ sudo ls > /media/CORSAIR/sds
bash: /media/CORSAIR/sds: Input/output error

```

@fsmithred:
Found it in `Notifications`(via search 'storage media'). It is easy from there on. But the name 'Notifications' is not very intuitive, so initially I excluded it (even as it was the only one showing up on my search results).
```
zbog@bogdan-duo:~$ ls -lt /media
total 24
drwxr-xr-x 9 zbog zbog    4096 2008-03-30 17:45 CORSAIR
drwxrwx--- 1 root plugdev 8192 2008-03-28 09:19 sda1
lrwxrwxrwx 1 root root       7 2008-01-01 20:30 floppy -> floppy0
drwxr-xr-x 2 root root    4096 2008-01-01 20:30 floppy0
lrwxrwxrwx 1 root root       6 2008-01-01 20:30 cdrom -> cdrom0
drwxr-xr-x 2 root root    4096 2008-01-01 20:30 cdrom0
drwxr-xr-x 9 zbog root    4096 [COLOR="Red"]1970-01-01[/COLOR] 02:00 CORSAIR-1

```

---

### Post by dstew on 2008-03-30
It looks like CORSAIR-1 mounted properly. Try ```
sudo touch /media/CORSAIR-1
```while it is mounted. That might change the date.

---

