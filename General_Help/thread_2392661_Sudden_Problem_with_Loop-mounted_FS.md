---
title: "Sudden Problem with Loop-mounted FS"
date: 2018-05-23
forum: General Help
---

### Post by bilkay on 2018-05-23
When I started up my laptop (16.04) this morning, it went into emergency mode. Perusing journalctl, I found that /home couldn't mount. My /home directory is an ext3-formatted file located on an NFS partition, which it's been for a long time. The fstab entry was as follows:

```
/host/Extended/Home.ext3 /home ext3 loop=/dev/loop2,errors=remount-ro 0    1
```

In emergency mode, I attempted to mount the file on /mnt and got an error message saying "device or resource busy". I found that I could mount it using /dev/loop3, so I changed to loop3 in fstab, restarted the laptop and all was apparently well.

I don't understand this at all. I didn't do an update recently or any other kind of change.

---

### Post by bilkay on 2018-05-24
Here's what's causing the device to be busy:

```
$ fuser -mv /dev/loop2
                     USER        PID ACCESS COMMAND
/dev/loop2:          root     kernel mount /snap/core/4650
```

Now I'd like to know why it just started out of the blue.

---

### Post by bilkay on 2018-05-24
```
$ mount |grep snap
/var/lib/snapd/snaps/core_4486.snap on /snap/core/4486 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/core_4571.snap on /snap/core/4571 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/core_4650.snap on /snap/core/4650 type squashfs (ro,nodev,relatime)
```


```
$ snap remove core --revision 4486
core removed
...
```

---

### Post by bilkay on 2018-05-24
Last thing: Removed loop option from fstab. This was a relic from an earlier time and is no longer necessary.

---

### Post by deadflowr on 2018-05-24
So from now on, be careful and watch out what you install, if you decide to install anything from Ubuntu Software.
As the Software store has snap packages mixed in with regular debian packages and if you install a snap package it'll reinstall core.
fer what it's wurth.

---

