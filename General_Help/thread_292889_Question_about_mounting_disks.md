---
title: "Question about mounting disks"
date: 2006-11-04
forum: General Help
---

### Post by frank05 on 2006-11-04
My /etc/fstab file has no entry for my floppy disk drive. However the "Gnome Disk Mounter" applet lets any user mount a floppy disk. How does it do this? Presumably it doesn't run as root!?

Can anybody explain this to me?

Thanks

---

### Post by chalex on 2006-11-04
Which version of Ubuntu?  Dapper or Edgy?

I don't know the answer, but I suspect it's different for the two versions, because they moved to using UUIDs for mounts or something.  You can try to look up udev/hotplug.

---

### Post by frank05 on 2006-11-04
Yeah I've moved to edgy. I can't remember if it was on my /etc/fstab in dapper. I have noticed the new uuids too.

---

### Post by chalex on 2006-11-04
I'm in Dapper still and there's no entry in fstab either.

---

### Post by matthewstory on 2006-11-04
you don't need the fstab to mount a drive, nor do you necissarily need to be root to mount a drive.  Check the permissions on the /dev/fd0 drive, it's probably set to allow mount from any.  The /etc/fstab file is merely there for the sake of convenience, it specifies the mount points and options for all volumes that are to be mounted at boot time . . . which the floppy drive should never be mounted at.

---

### Post by frank05 on 2006-11-05
> **matthewstory said:**
> it specifies the mount points and options for all volumes that are to be mounted at boot time . . . which the floppy drive should never be mounted at.

What you have said is true. Apart from the above. You can set a partition to be mounted when the user requests by specifying noauto and user options.

Thanks for the info about permissions on /dev/fd0. By default it appears to be rw by users in the group floppy. You have got me on the right track.

---

### Post by frank05 on 2006-11-05
I'm glad to say that "disc mounter" will default to any options you put into /etc/fstab . In the case of the floppy drive i wanted to use the sync option to speed up mounting time on a machine with lots of memory (i know that's not exactly what its there for, but it does the trick). It also allows you to mount the floppy from the command line concisely in the following way.

```
mount /media/floppy
```

fstab:

```

/dev/fd0        /media/floppy   auto    rw,noauto,user,sync    0       0

```

Trouble is, now every user can mount the floppy, not just those in 'floppy'. Anybody got any ideas how to restore this? Owner option will of course only allow root to mount. I haven't found any group option documented.

---

