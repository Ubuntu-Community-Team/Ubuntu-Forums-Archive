---
title: "How to disable drive for a particular user"
date: 2015-03-28
forum: General Help
---

### Post by click66 on 2015-03-28
I'm having a /mnt/data drive that I don't want to expose to other users. How can I disable that drive to even show up or that they can't mount it so that they can't see whats on it.

I've put these in my fstab:

```
/dev/disk/by-uuid/5E521E0E521DEC11 /mnt/data auto nosuid,nodev,gid=1000,nofail,x-gvfs-show 0 0

```

My users his group is 1000. Thought this would suffice but still when I login with another account the drive is mounted and the contents is also visible.

My group is different then the new created user.

Someone who could help me?

---

### Post by Morbius1 on 2015-03-28
From this:

> /dev/disk/by-uuid/5E521E0E521DEC11 /mnt/data auto nosuid,nodev,gid=1000,nofail,x-gvfs-show 0 0
To this:
> /dev/disk/by-uuid/5E521E0E521DEC11 /mnt/data auto nosuid,nodev,gid=1000**,[COLOR=#0000cd]umask=007[/COLOR]**,nofail,x-gvfs-show 0 0
Unmount the partition:
```
sudo umount /mnt/data
```
Then remount it with this:
```
sudo mount -a
```

umask represents the permissions you want to remove from the NTFS partition. A "0" represents none. A "7" represents everthing. So the resulting permissions on the mounted partition will be 770. Read writeable to root, and whoever is in group 1000 and inaccessible to everyone else.

Note: By default NTFS will mount with "umask=000" so you specified the group but it's still accessible to everyone unless you override umask with your own setting.

---

### Post by click66 on 2015-03-29
Thank you so much. Works like a charm :).

---

