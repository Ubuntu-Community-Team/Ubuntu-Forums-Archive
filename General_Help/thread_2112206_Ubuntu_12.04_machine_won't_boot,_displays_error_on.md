---
title: "Ubuntu 12.04 machine won't boot, displays error on start"
date: 2013-02-04
forum: General Help
---

### Post by andrewneely on 2013-02-04
I am running Ubuntu 12.04 running Cinnamon desktop. When booting, the startup information displays until I receive this error, and the system halts.  I first thought it was a crontab I recently added, but was able to remove it, and still have this issue.  Please help!  This is an Edubuntu install running 12.04, with lxde, kde, unity, and cinnamon desktops.  

```
 Starting nanny (Parental Control Daemon):
/usr/lib/python2.7/dis-packages/gtk-2.0/gtk/__init.py:57:  GtkWarning:
 could not open display warnings.warn(str(e), _gtk.warning)
 ** (twistd:2023):  Warning**: Command line'dbus-launch --autolaunch-0e42ec90e8137a7c8d6a1cc00000005 --binary-syntax --close-strerr' exited with non-zero exit status1: Autolaunch error: x!! initialization failed.\n
```

---

### Post by omeomi on 2013-02-04
Can you boot using [Recovery mode]("https://wiki.ubuntu.com/RecoveryMode")?

---

### Post by andrewneely on 2013-02-04
Yes, I can boot to the recovery menu.  Any action I take which mounts the file system in read/write mode displays a message from  fsck and then it hangs.

I can access the drive in question from boot the root prompt and by booting via a live CD.

---

