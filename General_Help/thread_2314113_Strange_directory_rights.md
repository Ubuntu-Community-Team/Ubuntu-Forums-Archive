---
title: "Strange directory rights"
date: 2016-02-18
forum: General Help
---

### Post by Finarfin on 2016-02-18
Hi,

I have one directory(gvfs in listing) which has really strange rights:

[HTML]root@ubuntu:/run/user/1000# ls -la
ls: cannot access gvfs: Permission denied
total 16
drwx------ 10 jwasilew jwasilew 280 lut 18 09:45 .
drwxr-xr-x  3 root     root      60 lut 18 09:47 ..
-rw-rw-r--  1 jwasilew jwasilew  60 lut 18 09:45 dbus-session
drwx------  2 jwasilew jwasilew  60 lut 18 16:32 dconf
d?????????  ? ?        ?          ?            ? gvfs
drwx------  2 jwasilew jwasilew  40 lut 18 09:45 gvfs-burn
drwx------  2 jwasilew jwasilew 120 lut 18 09:45 keyring
drwx------  2 jwasilew jwasilew  80 lut 18 09:45 pulse
drwxr-xr-x  2 jwasilew jwasilew  80 lut 18 09:45 systemd
drwx------  2 jwasilew jwasilew  40 lut 18 16:18 unity
drwx------  3 jwasilew jwasilew  60 lut 18 09:45 upstart
-rw-r--r--  1 jwasilew jwasilew   5 lut 18 09:45 upstart-dbus-bridge.1704.pid
-rw-r--r--  1 jwasilew jwasilew   5 lut 18 09:45 upstart-file-bridge.1704.pid
-rw-r--r--  1 jwasilew jwasilew   5 lut 18 09:45 upstart-udev-bridge.1704.pid
[/HTML]

What I would like to say, it's that I'm inside root account, so that situation should not have a place. I'm asking, about that directory cause from time to time I have a problem with samba directories. One time I'm able to copy something to my samba drive and other day I'm not able to do this, EVEN when I'm able to browse everything on that drive and I'm ABLE to remove files from that shared drive. So it's not because of permission. That's why I'm asking about this strange-rights.

Someone has a clue what is that?
At least I found that description:
[http://unix.stackexchange.com/questions/77453/why-cannot-find-read-run-user-1000-gvfs-even-though-it-is-running-as-root](http://unix.stackexchange.com/questions/77453/why-cannot-find-read-run-user-1000-gvfs-even-though-it-is-running-as-root)

but trying to umount gvfs finished with:
[HTML]
/run/user/1000$ umount /run/user/1000/gvfs 
umount: /run/user/1000/gvfs: Permission denied
[/HTML]
Even when I'm doing it as user 1000.

Thanks in advance for help with that!

---

### Post by steeldriver on 2016-02-18
What you're seeing is normal, AFAIK

Things mounted by the gnome virtual filesystem (gvfs) are user-mounts: root has no business knowing anything about them. Typically they're things like network shares that you've mounted using "Browse network" or "Connect to server" from the nautilus filemanager

You should be able to unmount them from the command line using gvfs-mount -u (or gvfs-mount --unmount) e.g.

```

$ ls -l /run/user/1006/gvfs
total 0
drwx------ 1 steeldriver steeldriver 0 Jun 16  2013 smb-share:server=nas-01,share=media
$ 
$ gvfs-mount --unmount "smb://nas-01/media/"
$ 
$ ls -l /run/user/1006/gvfs
total 0

```

---

