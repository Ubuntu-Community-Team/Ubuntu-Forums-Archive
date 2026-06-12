---
title: "Changing the mount permissions so that other users besides root can modify files"
date: 2007-06-18
forum: General Help
---

### Post by Gizim on 2007-06-18
I have 2 mount points /media/storage and /media/docs they are both set to root as the owner so i can not add new files unless i am under the console and as su. How in fstab do i change it so that anybody on the system can modify files?



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6bd01f38-ef29-4d1b-a0b0-8ec07c8b3b8f /               ext3    defaults,errors=remount-ro 0 $
# /dev/sda3
UUID=2046d2a1-670a-4be0-b1f7-fd9f237c1366 /media/docs     ext3    defaults        0       2
# /dev/sda4
UUID=ae84f522-213f-44aa-a327-c5696ab4dc66 /media/storage  ext3    defaults        0       2
# /dev/sda2
UUID=48a539f1-b249-f099-8640-f563b642c6d0 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by dreadlord_chris on 2007-06-18
> **Gizim said:**
> I have 2 mount points /media/storage and /media/docs they are both set to root as the owner so i can not add new files unless i am under the console and as su. How in fstab do i change it so that anybody on the system can modify files?



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6bd01f38-ef29-4d1b-a0b0-8ec07c8b3b8f /               ext3    defaults,errors=remount-ro 0 $
# /dev/sda3
UUID=2046d2a1-670a-4be0-b1f7-fd9f237c1366 /media/docs     ext3    defaults        0       2
# /dev/sda4
UUID=ae84f522-213f-44aa-a327-c5696ab4dc66 /media/storage  ext3    defaults        0       2
# /dev/sda2
UUID=48a539f1-b249-f099-8640-f563b642c6d0 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

My mount points are owned by root too - but I can add files to them without any problems. And your fstab looks fine. I have a feeling it's your mount points themselves that are the problem. Try this:
```

sudo chmod 777 /media/storage
sudo chmod 777 /media/docs

```

This will set permissions to that everybody can read/write/execute the contents of those mount points.

---

### Post by marc321 on 2007-06-18
Actually, I think it might be preferable to use the "user" option in the fstab file.

Try this:

```

# /dev/sda3
UUID=2046d2a1-670a-4be0-b1f7-fd9f237c1366 /media/docs ext3 defaults,user 0 2
# /dev/sda4
UUID=ae84f522-213f-44aa-a327-c5696ab4dc66 /media/storage ext3 defaults,user 0 2

```

Notice I appended ",user" to "defaults".  This is how I do it in Slackware.  On my system, prior to mounting my thumb drive, it is owned by root with 755 (rwxr-xr-x) permissions.  When I mount as a regular user (no sudo needed), the ownership of the mountpoint is automatically changed to myusername:users rather than root:root.

Hope this helps.

---

### Post by dreadlord_chris on 2007-06-18
> **marc321 said:**
> Actually, I think it might be preferable to use the "user" option in the fstab file.

Try this:

```

# /dev/sda3
UUID=2046d2a1-670a-4be0-b1f7-fd9f237c1366 /media/docs ext3 defaults,user 0 2
# /dev/sda4
UUID=ae84f522-213f-44aa-a327-c5696ab4dc66 /media/storage ext3 defaults,user 0 2

```

Notice I appended ",user" to "defaults".  This is how I do it in Slackware.  On my system, prior to mounting my thumb drive, it is owned by root with 755 (rwxr-xr-x) permissions.  When I mount as a regular user (no sudo needed), the ownership of the mountpoint is automatically changed to myusername:users rather than root:root.

Hope this helps.

The *user* option allows ordinary (non-admin) users to mount the filesystem - and updates **mtab** and the mount point perms - to reflect the user that mounted it. I can see that being useful for *external* drives *that are mounted dynamically* - but for internal drives *that get mounted at boot* - it's still gonna be root that is mounting them.

---

### Post by marc321 on 2007-06-18
> **dreadlord_chris said:**
> The *user* option allows ordinary (non-admin) users to mount the filesystem - and updates **mtab** and the mount point perms - to reflect the user that mounted it. I can see that being useful for *external* drives *that are mounted dynamically* - but for internal drives *that get mounted at boot* - it's still gonna be root that is mounting them.
Ahh, yes.  I forgot about the fact that the partitions/drives in question are mounted at boot.  You'd have to unmount as root, then mount again as a user.  Oops.

Also, I noticed "defaults,user" is a contradiction, since "defaults" implies "nouser".

Well, I'm an idiot today.

The only thing that bothered me was changing the permissions to 777.  Whenever I see 777, I think "world writable, not good."  That may be old mentality on my part.  I should just be quiet and watch this thread.  Maybe I'll learn a thing or two.  :-)

---

### Post by marc321 on 2007-06-18
> Perhaps appending "gid=100,umask=007" to "defaults" would be another option. This would set the mount point group to users (100) and change the permissions to 770.  These settings will be effective at boot, eliminating the need to change permissions every time you reboot or unmount/remount.

EDIT: Please ignore the above post.  I am *really* being an idiot today.  The umask option only applies to fat32 and ntfs filesystems. :oops:

---

### Post by vanadium on 2007-06-18
Instead of fiddling with the mount permissions, do it in the real Unix/Linux way. As root, create a few directories on that drive, change owner to the respective users, then create a link to these directorie in the user's home folders, such that they have fast and convenient access to them from within their home folders.

---

### Post by dreadlord_chris on 2007-06-18
> **marc321 said:**
> Ahh, yes.  I forgot about the fact that the partitions/drives in question are mounted at boot.  You'd have to unmount as root, then mount again as a user.  Oops.

Also, I noticed "defaults,user" is a contradiction, since "defaults" implies "nouser".

Well, I'm an idiot today.

The only thing that bothered me was changing the permissions to 777.  Whenever I see 777, I think "world writable, not good."  That may be old mentality on my part.  Maybe I'll just be quiet and watch this thread; learn a thing or two.  :-)

actually, it's not a contradiction - the *user* following *defaults* just overrides the *implied nouser*

The only reason that I suggested chmoding the folders was because those are the perms that mine show - I didn't change them to that, that's just how it set up.

Since these are 'storage' partitions - and the OP said they wanted **anybody** to be able to access/modify their contents, seems to me this is the easiest solution.

---

