---
title: "&quot;inotify watch limit reached&quot;, but it's not true?"
date: 2022-12-25
forum: General Help
---

### Post by clepsdyrae on 2022-12-25
When I install a .deb file (dpkg -i, installing the MuseHub application from the recent MuseScore release), I get this error:

```
Failed to add a watch for /run/systemd/ask-password: inotify watch limit reached
```

Googling leads me to understand that this means the inotify kernel subsystem for watching for file changes has exceeded it's cap. My cap:

```
$ cat /proc/sys/fs/inotify/max_user_watches
123014
```

I downloaded, compiled, and ran the [inotify-info utility]("https://github.com/mikesart/inotify-info"), which shows that I'm nowhere near the limit:

```
$ _release/inotify-info 
------------------------------------------------------------------------------
INotify Limits:
  max_queued_events    16384
  max_user_instances   128
  max_user_watches     123014
------------------------------------------------------------------------------
        Pid  App                        Watches   Instances
       18264 xdg-desktop-portal-gtk          80   1
        3026 kded5                           66   3
        3075 plasmashell                     52   3
        2879 systemd                         47   3
       18138 thunderbird                     10   2
       18169 firefox                          6   2
...
        3139 dbus-daemon                      1   1
        3090 gmenudbusmenuproxy               1   1
        2898 pipewire-media-session           1   1
------------------------------------------------------------------------------
Total inotify Watches:   337
Total inotify Instances: 57
------------------------------------------------------------------------------

```

Can anyone help me reconcile this situation? Is it possible that this is something unique to this .deb, and I should take it up with those developers? Thanks!

---

