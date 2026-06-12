---
title: "how to change mount point"
date: 2008-05-13
forum: General Help
---

### Post by joe281180 on 2008-05-13
Hi,

I've just installed ubunutu and I've changed the mount point for one of my drives to an invalid location so now I can't mount it.

With the drive mounted, I opened the properties for the drive. The mount point field was blank so I typed in a folder location thinking that would mount the drive at that location.

But now when I try to mount the drive I get an error message saying that the mount point is invalid because it contains a forward slash, however I can't change it because without mounting the drive I don't know how to access the properties for it.

I'm using 8.04 by the way, 

many thanks,
Joe

---

### Post by hermes0710 on 2008-05-13
Can you post the contents of /etc/fstab? What is the name of the device in fstab?

---

### Post by smoker on 2008-05-13
you have to create a mount point, then edit your fstab so that your partition is mounted there,

have a look at his thread, explains it better than i can.
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

just substitute 'windows' for what ever you want to mount

---

### Post by clint1010 on 2008-05-30
I did the same thing for an internal drive, and got the same problem.

using
```
gconf-editor
```
to modify the key "/system/storage/volumes/_org_freedesktop_Hal_devices_voume_uuid_*/mount_point" (I just deleted the mount point I set)

I managed to fix the problem

See [this link]("https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/107668") for more detail and info

:popcorn:

---

