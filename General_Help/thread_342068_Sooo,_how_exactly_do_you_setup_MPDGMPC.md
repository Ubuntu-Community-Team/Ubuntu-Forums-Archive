---
title: "Sooo, how exactly do you setup MPD/GMPC?"
date: 2007-01-19
forum: General Help
---

### Post by Phixion on 2007-01-19
```
mark@fame:~$ sudo apt-get install install mpd mpc gmpc
```

```
Unpacking mpd (from .../mpd_0.12.1-1ubuntu1_i386.deb) ...
Setting up mpd (0.12.1-1ubuntu1) ...
Stopping Music Player Daemon: not running or no pid_file set.
Starting Music Player Daemon: creating /var/lib/mpd/tag_cache... unable to bind port 6600: Address already in use
maybe MPD is still running?
failed.
```

```
mark@fame:~$ sudo dpkg-reconfigure mpd
unable to bind port 6600: Address already in use
maybe MPD is still running?
```

Can anyone point me in the right direction please? I'm trying to follow this guide: [http://www.ubuntuforums.org/showthread.php?t=31763&highlight=mpd+howto](http://www.ubuntuforums.org/showthread.php?t=31763&highlight=mpd+howto)

Please help.

Thanks!

---

### Post by Phixion on 2007-01-19
Bump, anyone able to help or is this a lost cause?

---

### Post by xabbott on 2007-01-22
Could try mpd --kill or manually killing the process (**killall mpd**). Also I suggest checking out
[http://mpd.wikia.com/wiki/Getting_Started](http://mpd.wikia.com/wiki/Getting_Started)

---

