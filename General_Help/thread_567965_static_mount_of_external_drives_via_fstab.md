---
title: "static mount of external drives via fstab"
date: 2007-10-05
forum: General Help
---

### Post by frog_pilot on 2007-10-05
I haven't found yet any possibility to mount external drives to static mount-points with special mount-options in feisty.

In Edgy these entrys in my fstab worked well:```
# external drives
# USB
# /dev/sda1
UUID=24942821-cc0d-4ca3-8528-bcc951f86ce8 /media/ext_data        ext3    user,rw,auto        0       0
# /dev/sda2
UUID=66E444A632ECD092   /media/ext_ntfs  ntfs-3g  user,auto,uid=1000,gid=1000,locale=de_DE.utf8    0    0
# 
# FIREWIRE
# /dev/sdb6
UUID=31B1F9FB83C3480B   /media/fiwiboot   hfsplus  user,ro,noauto 	0    0
# /dev/sdb3
UUID=46492E39859A1DEB   /media/OS_X_live   hfsplus  user,ro,auto 	0    0
# /dev/sdb5
UUID=EC58742925CDF13E   /media/MAC_DATA   hfsplus  user,ro,auto 	0    0
# /dev/sdb7
UUID=91C11029794170B4   /media/LIN_DATA   hfsplus  user,rw,auto,uid=0,gid=46,umask=022,nls=utf8 	0    0
## End of external drives
```

But in Feisty the external volumes will only mount when there is no special entry for them in fstab. With these mentioned entries the external drives won't mount at all. When I execute ```
sudo mount -a
``` I can access the drives via the mount points (go to the folders in the media-directory) but the volumes aren't displayed on my desktop or in the places-list of nautilus.

How can I/ do you manage the static mount of external drives with feisty? Thanks in advance for your help... :)

---

### Post by Izkata on 2007-10-24
I had the exact same problem in Feisty, and am still having it in Gutsy, while it worked fine back in Edgy.

Any help?

---

### Post by frog_pilot on 2007-10-24
I changed the mount options of the external drives. I substituted ```
user,auto
``` with ```
users,noauto
```. Now the drives mount automatically, but I can only unmount them as root (sudo umount <mount point>). No idea why. With option users every user of the group plugdev could mount/ unmount the drive :confused: the noauto option is better for external drives, because the auto-option is for mounting on system start...

Try it and tell me your results. - but it's still weird, that it worked fine in edgy, but not on the newer releases. Maybe it's due to a new procedure/ program for mounting external devices...

---

### Post by Izkata on 2007-10-24
Still not mounting automatically for me.  And "sudo mount -a" only works with the "auto" option...

---

### Post by frog_pilot on 2007-10-27
Yes its true, "sudo mount -a" only works with the auto option. And I have mentioned that only my ext3-volume will be mounted automatically. On the usb-drive there is also a ntfs-volume. This one I have to mount manually.
But for my firewire drive it works fine. There are 4 volumes on it and these volumes will mount after plugging in with the desired options (these are all hfs+-volumes).
But as stated umount only works as root :confused:

---

### Post by dcstar on 2007-10-27
> **frog_pilot said:**
> I haven't found yet any possibility to mount external drives to static mount-points with special mount-options in feisty.
........
How can I/ do you manage the static mount of external drives with feisty? Thanks in advance for your help... :)

If you want external partitions mounted on the same place every time, the simplest thing to do is to give each partition a label, then they will always be mounted in /media/LABEL.

The tools to label each partition can be different for each partition type (be VERY careful using them!)

---

### Post by frog_pilot on 2007-10-27
> **frog_pilot said:**
> I haven't found yet any possibility to mount external drives to static mount-points with **special mount-options** in feisty.

When I only label my ntfs-volume it will only be mounted with ntfs-driver and not with ntfs-3g and it's the same with my hfs+ volumes. They mount also ro, when there is no entry in fstab. And in fstab (as posted above) I use UUIDs and there are already labels for the volumes for my other OSes.

In edgy it was no problem to mount external drives with special options via an entry in fstab. Since feisty it isn't working that good.

When I plug in an external drive, it will mount now, but I don't have the permission to unmount it and my ntfs-volume won't mount at all. I need to be root to mount the ntfs-volume and to unmount all the other volumes on my external drives. But I set the mount options to "users". That means anybody can mount the volumes and anybody (not only the user who mounted them) can unmount them. But it isn't working like this... :confused:

---

### Post by syxbit on 2007-10-27
one thing of interest.
my ext3 USB drive auto mounted on boot in dapper, and i edgy, but stopped in feisty and gutsy.
however, i recently installed gutsy x64, and it automounts.
weird

---

