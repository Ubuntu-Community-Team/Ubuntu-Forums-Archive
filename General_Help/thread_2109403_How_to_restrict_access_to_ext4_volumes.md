---
title: "How to restrict access to ext4 volumes"
date: 2013-01-27
forum: General Help
---

### Post by Rebelli0us on 2013-01-27
With NTFS volumes you can restrict access to other users by adding "uid=1000,umask=077" to FSTAB options. How do you do that with ext4 volumes?


```
UUID=B2C86616C875D4DC /media/Win7 ntfs-3g defaults,**uid=1000,umask=077**,locale=en_US.utf8 0 0
```

---

### Post by thermion on 2013-01-27
In case of an ext4 volume, you have to restrict access via permission and user/group ownership.

---

### Post by mcduck on 2013-01-27
Simply change the permissions (and ownership) of the files & directories themselves. You only need to do that in fstab for NFTS drives because they can't store the permissions.

For example if the Ext partition is mounted in /media/yourdrive, and you want to limit the access to the whole partition to your user only, even excluding your group:
```

sudo chown username:usergroup /media/yourdrive
sudo chmod 700 /media/yourdrive

```
(replace username:usergroup with the correct name & group)

---

### Post by Rebelli0us on 2013-01-27
> **mcduck said:**
> Simply change the permissions (and ownership) of the files & directories themselves. You only need to do that in fstab for NFTS drives because they can't store the permissions.

For example if the Ext partition is mounted in /media/yourdrive, and you want to limit the access to the whole partition to your user only, even excluding your group:
```

sudo chown username:usergroup /media/yourdrive
sudo chmod 700 /media/yourdrive

```
(replace username:usergroup with the correct name & group)

Thank you. The partition contains a complete OS. In my past experience, if you take ownership away form root the OS simply stops working.

---

### Post by thermion on 2013-01-27
In this case, you only modify the permissions of the specific files and folders.

---

### Post by mcduck on 2013-01-27
> **Rebelli0us said:**
> Thank you. The partition contains a complete OS. In my past experience, if you take ownership away form root the OS simply stops working.
YOu are correct you definitely don't want to change the permissions of Linux system directories.

Is there any reaason why you need to even mount the partition on boot?

If you actually don't need it always mounted, you could just configure it in fstab with the "noauto" and "nouser" options to prevent automount from mounting it. That would mean that users would need to use the mount command to access the partition, and doing that would require sudo permissions... (Which I assume they don't have, since if they do, there's nothing you can do to prevent them accessing anything on the machine).

---

### Post by Rebelli0us on 2013-01-27
> **mcduck said:**
> YOu are correct you definitely don't want to change the permissions of Linux system directories.

Is there any reaason why you need to even mount the partition on boot?

If you actually don't need it always mounted, you could just configure it in fstab with the "noauto" and "nouser" options to prevent automount from mounting it. That would mean that users would need to use the mount command to access the partition, and doing that would require sudo permissions... (Which I assume they don't have, since if they do, there's nothing you can do to prevent them accessing anything on the machine).

It's auto-mounted at boot in fstab because my apps use it. I just want it to be invisible to other users, just as I do with NTFS volumes.  Is there a way to do that with an entire ext4 partition?

---

### Post by mcduck on 2013-01-27
Well, you could mount in inside a directory which is only available to your user account. 

Make a directory inside /mnt, set that directory's ownership & permissions so only you can access it, then create another directory inside it and use that as the mount point for your partition.

That way you wouldn't have to touch the permissions of the partition itself at all.

---

### Post by Rebelli0us on 2013-01-27
> **mcduck said:**
> Well, you could mount in inside a directory which is only available to your user account. 

Make a directory inside /mnt, set that directory's ownership & permissions so only you can access it, then create another directory inside it and use that as the mount point for your partition.

That way you wouldn't have to touch the permissions of the partition itself at all.

Thank you. Now it's mounted as usual in /media/..., nautilus calls it "folder (inode/directory)" that's like a symbolic link? What if I just take ownership of the link instead of moving it to /mnt?

---

### Post by mcduck on 2013-01-27
> **Rebelli0us said:**
> Thank you. Now it's mounted as usual in /media/..., nautilus calls it "folder (inode/directory)" that's like a symbolic link? What if I just take ownership of the link instead of moving it to /mnt?

You definitely don't want to mess with the ownership of /media, that would break all automatic mounting for every user. And changing the ownership of the mount point (it's just a directory, not a link by the way) would change the ownership of the partition itself. Which you said you don't want to do since it's the root of some OS...

And I recommended using folder inside /mnt since that way the mounted partition won't appear automatically on file managers (and/or desktops) of all the users, which would happen when mounted in /media. Much cleaner to keep things people can't use away from their desktops... ;)

---

### Post by Rebelli0us on 2013-01-28
> **mcduck said:**
> You definitely don't want to mess with the ownership of /media, that would break all automatic mounting for every user. And changing the ownership of the mount point (it's just a directory, not a link by the way) would change the ownership of the partition itself. Which you said you don't want to do since it's the root of some OS...

And I recommended using folder inside /mnt since that way the mounted partition won't appear automatically on file managers (and/or desktops) of all the users, which would happen when mounted in /media. Much cleaner to keep things people can't use away from their desktops... ;)

Thank you. I'm sorry I wasn't clear in what I posted, I didn't mean taking ownership of /media. I meant to mount the ext4 volume under /media/**Ubuntu12** for example.  **Ubuntu12** is a symbolic link to the mounted volume? What's the difference between mounting under /media or /mnt? It seems the same, both are some kind of a pointer to the volume.

---

### Post by mcduck on 2013-01-28
> **Rebelli0us said:**
> Thank you. I'm sorry I wasn't clear in what I posted, I didn't mean taking ownership of /media. I meant to mount the ext4 volume under /media/**Ubuntu12** for example.  **Ubuntu12** is a symbolic link to the mounted volume? What's the difference between mounting under /media or /mnt? It seems the same, both are some kind of a pointer to the volume.

the only difference is that anything mounted under /media will appear on graphical file managers etc, just like what happens when you insert a CD or plug in an USB drive. 

Anyway, changing the ownership of the mount point is the same as changing the ownership of the partition mounted on that mount point. So if the partition is a root partition of another OS, you'd change the ownership of the root directory of that OS. Which you probably don't want to do. Which is why I suggested using one more layer of directory hierarchy to avoid messing with the ownership & permissions of your Ubuntu system directories or the permissions of the partition you are mounting.

(And no, in your example /media/ubuntu12 wouldn't be a symbolic link  or any kind of pointer to the mounted media, it would be *the* root directory of the mounted media. A symbolic link is quite a different thing.)

---

### Post by Rebelli0us on 2013-01-30
> **mcduck said:**
> the only difference is that anything mounted under /media will appear on graphical file managers etc, just like what happens when you insert a CD or plug in an USB drive. 

Anyway, changing the ownership of the mount point is the same as changing the ownership of the partition mounted on that mount point. So if the partition is a root partition of another OS, you'd change the ownership of the root directory of that OS. Which you probably don't want to do. Which is why I suggested using one more layer of directory hierarchy to avoid messing with the ownership & permissions of your Ubuntu system directories or the permissions of the partition you are mounting.

(And no, in your example /media/ubuntu12 wouldn't be a symbolic link  or any kind of pointer to the mounted media, it would be *the* root directory of the mounted media. A symbolic link is quite a different thing.)


Thank you. If I open nautilus as root, right-click on the mounted OS volume, select Proprties > Permissions, and set "Group" to myself and "Others" to **none**, will that accomplish the same?

---

### Post by mcduck on 2013-01-30
> **Rebelli0us said:**
> Thank you. If I open nautilus as root, right-click on the mounted OS volume, select Proprties > Permissions, and set "Group" to myself and "Others" to **none**, will that accomplish the same?

Well, once again you'd end with the problem you mentioned yourself that you wanted to avoid, changing the ownership of the root of another OS partition...

> 
Thank you. The partition contains a complete OS. In my past experience, if you take ownership away form root the OS simply stops working.


Changing the ownership or permissions of the mount point of a mounted filesystem is exactly the same as changing the permission of the fileystem itself.

(Ignoring any issues that might cause to the other OS, then yes, doing that would work as a way of restrictying access by other users. Which is why I suggested doing that in my first reply to this thread, before you mentioned that it's the root partition of some other OS...)

---

### Post by Rebelli0us on 2013-01-30
> **mcduck said:**
> Well, once again you'd end with the problem you mentioned yourself that you wanted to avoid, changing the ownership of the root of another OS partition...



Changing the ownership or permissions of the mount point of a mounted filesystem is exactly the same as changing the permission of the fileystem itself.

(Ignoring any issues that might cause to the other OS, then yes, doing that would work as a way of restrictying access by other users. Which is why I suggested doing that in my first reply to this thread, before you mentioned that it's the root partition of some other OS...)

Thank you for your patience, I'm looking for a simple solution that's not too technical, that anyone can use.

The Permissions tab in Properties shows **Owner**, **Group** and **Others**. I was proposing to leave root as owner and change the other two. I'm just reluctant to experiment because I've pooched OSes before trying to do this.:popcorn:

---

### Post by mcduck on 2013-01-30
The simple, safe and not technical solution would be the one I already suggested, not changing the ownership or permissions of the mount point, but instead one directory above it.

For example, /mnt/Restricted/Ubuntu12, and then use the "Ubuntu12" as the mount point, but change the permissions of the "Restricted". 

(And yes, if you really want you *can* do the same inside /media instead of /mnt, if you really want the "Restricted" to appear on every user's desktops/file managers even though they can't access it.)

---

### Post by Rebelli0us on 2013-01-31
> **mcduck said:**
> The simple, safe and not technical solution would be the one I already suggested, not changing the ownership or permissions of the mount point, but instead one directory above it.

For example, /mnt/Restricted/Ubuntu12, and then use the "Ubuntu12" as the mount point, but change the permissions of the "Restricted". 

(And yes, if you really want you *can* do the same inside /media instead of /mnt, if you really want the "Restricted" to appear on every user's desktops/file managers even though they can't access it.)

Thank you that works.

I opened nautilus as root and created a new directory “ext4” under /media. Selected the new directory > Properties > Permissions, and set “Owner” and "Group" to myself and for "Others" I set access to “none”.

Then I opened /etc/fstab and edited the existing entry by adding the new directory to the path:  /media/ubuntu12  -->  /media/**ext4**/ubuntu12 

For all apps pointing to the volume I changed the paths accordingly.

Rebooted. Done.

The volume does NOT show in user's desktops/file managers and if they navigate to /media/ext4 they get “access denied” (just like in the NTFS method above).

I like this method because it’s as simple as the NTFS solution and does NOT change any file attributes in the protected volume? (I assume Linux security settings are just like file attributes in NTFS.)

---

