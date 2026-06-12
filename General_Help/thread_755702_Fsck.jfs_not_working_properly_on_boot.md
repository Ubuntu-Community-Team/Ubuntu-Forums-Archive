---
title: "Fsck.jfs not working properly on boot"
date: 2008-04-15
forum: General Help
---

### Post by Pensive Koala on 2008-04-15
Like a few other users on these forums and elsewhere, I've had problems with my JFS install of Ubuntu mounting read-only after a crash.  I figured out a fix (manual fsck, then manual remount), but I have to do it every single time I boot.  Is there a way to actually fix the problem so that it automatically fsck's on boot?  I have /etc/fstab set up to fsck the filesystem at mount, but for some reason that isn't cutting it.

---

### Post by gasull2 on 2008-05-19
> **Pensive Koala said:**
> Like a few other users on these forums and elsewhere, I've had problems with my JFS install of Ubuntu mounting read-only after a crash.  I figured out a fix (manual fsck, then manual remount), but I have to do it every single time I boot.  Is there a way to actually fix the problem so that it automatically fsck's on boot?  I have /etc/fstab set up to fsck the filesystem at mount, but for some reason that isn't cutting it.

Hi, anybody still there? :)  This post is from 4 weeks ago, but I guess there are more people having this problem, like me.

Well, I just had the same problem and it went away when I fixed my /etc/fstab line from
```
UUID=6bc031bf-50e0-446d-b308-a682677d9fb4 /               jfs     relatime,errors=remount-ro,user_xattr 0
```
to
```
UUID=6bc031bf-50e0-446d-b308-a682677d9fb4 /               jfs     relatime,errors=remount-ro 0
```

So I suppressed the user_xattr property.  I put it there in the beginning because I wanted to [enable extended attributes for Beagle]("http://beagle-project.org/Enabling_Extended_Attributes").

I think the problem was that the kernel wasn't compiled for the extended attributes and then mounted the partition as read-only.

Are you using Beagle too? Then you might need to compile the kernel as explained in the link above, if you want to use extended attributes.

Hope this helps.

---

### Post by Pensive Koala on 2008-05-27
I'm still here, and no, no beagle...I've since reinstalled to just not use JFS.  Pity, since I prefer it to ext3, but this was too big a hassle.

---

