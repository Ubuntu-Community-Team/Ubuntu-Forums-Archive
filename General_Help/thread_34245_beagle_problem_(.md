---
title: "beagle problem :("
date: 2005-05-14
forum: General Help
---

### Post by woodb on 2005-05-14
Is anyone else seeing this when running beagle:

woodb@swr512:~$ beagled
woodb@swr512:~$ ioctl: Bad address
ioctl: Bad address
ioctl: Bad address

Unhandled Exception: System.IO.IOException: Attempt to watch /usr/share/applications failed!
in <0x00133> Beagle.Util.Inotify:Watch (System.String path, EventType mask, EventType initial_filter)
in <0x0000f> Beagle.Util.Inotify:Watch (System.String path, EventType mask)
in <0x00167> Beagle.Daemon.LauncherQueryable.LauncherQueryable:Watch (System.String path)
in <0x00158> Beagle.Daemon.LauncherQueryable.LauncherQueryable:Start ()
in <0x00016> Beagle.Daemon.Queryable:Start ()
in <0x000af> Beagle.Daemon.QueryDriver:Start ()
in <0x00b9b> Beagle.Daemon.BeagleDaemon:Main (System.String[] args)


I followed the instructions on the beaglewiki page.. but it appears that I have an inotify issue?  Perhaps something to do with the inotify version (how do you check this?)

Any help would be appretiated!

TIA,
Brendan

---

### Post by Knome_fan on 2005-05-14
Hi,
what kernel are you using? 
If you are using the stock hoary kernel you should probably try to run beagle without inotify, as the inotify version that comes with this kernel has some issues.

Beagle runs fine for me without inotify here, btw.

---

