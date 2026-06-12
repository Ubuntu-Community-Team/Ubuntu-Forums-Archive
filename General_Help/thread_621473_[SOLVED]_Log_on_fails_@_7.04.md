---
title: "[SOLVED] Log on fails @ 7.04"
date: 2007-11-23
forum: General Help
---

### Post by theredspecial on 2007-11-23
the main sympton of my problem is: I cannot logon to my Ubuntu 7.04 with Xfce.

Situation
First I removed an user from the system, this account has not been used for several weeks. It was not the first or primary account of the system. Moreover, today I installed the ICA 10.6 client (haven't seen it working though) and tried to upgrade to 7.10 - this failed as the update manager could not download 2 files (forgotten the details) (after reading a few posts here, I might reconsider this).

After this: i have not been able to login.

Recovery modes and safe modes don't work either.

When trying to login (normal session) the following error pops up:
```

/etc/gdm/PreSession/Default: Registering your sessions with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -u "/var/lib/gdm/:0.Xservers"-h ""-l ":0" "robert"
/etc/gdm/Xsession: Beginning session setup...
/etc/X11/Xsession.d/40guidance-displayconfig_restore: 11: /usr/bin/displayconfig-restore: not found
/usr/bin/xmodmap: unable to open file 'usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap: 1 error encoutered, aborting.
/usr/bin/startxfce4: X server already running on display :0
xfce4-session: Unable to access file /home/robert/.ICEauthority: Access denied

```

\
Now, if I try a GNOME safe mode session, the error message is:
```

/etc/gdm/PreSession/Default: Registering your sessions with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -u "/var/lib/gdm/:0.Xservers"-h ""-l ":0" "robert"
(gnome-session:5926): libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: Access denied
Cannot create GNOME configuration file of user '/home/robert./gnome2': Access denied

```

This last sentence is my translation - btw

I've also tried a recovery mode boot, but as I'm a newbie I wasn't really sure what to do

any advice?

I checked the forum, but could not find a fitting post

---

### Post by theredspecial on 2007-11-24
did some more searching at this forum and this post [http://ubuntuforums.org/showthread.php?t=621142](http://ubuntuforums.org/showthread.php?t=621142) solved my problem

---

