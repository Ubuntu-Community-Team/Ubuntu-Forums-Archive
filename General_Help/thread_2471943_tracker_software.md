---
title: "tracker software"
date: 2022-02-14
forum: General Help
---

### Post by mlempenau on 2022-02-14
I would appreciate it if someone would explain to me what is going on with the boot up code below.  It's talking about a tracker and and free desktop.  I'm assuming this is just some tracking I have to put up with but am not sure.  Thanks for your help.  

  	 	 	 	   2/13/22 6:05 PM	systemd	app-gnome-update\x2dmanager-2394.scope: Deactivated successfully.
 2/13/22 6:05 PM	systemd	app-gnome-update\x2dmanager-2394.scope: Consumed 4.330s CPU time.
 2/13/22 6:05 PM	dbus-daemon	[session uid=1000 pid=1630] Activating via systemd: service name='org.freedesktop.Tracker3.Miner.Extract' unit='tracker-extract-3.service' requested by ':1.8' (uid=1000 pid=1659 comm="/usr/libexec/tracker-miner-fs-3 " label="unconfined")
 2/13/22 6:05 PM	systemd	Starting Tracker metadata extractor...
 2/13/22 6:05 PM	dbus-daemon	[session uid=1000 pid=1630] Successfully activated service 'org.freedesktop.Tracker3.Miner.Extract'
 2/13/22 6:05 PM	systemd	Started Tracker metadata extractor.
 2/13/22 6:05 PM	PackageKit	search-file transaction /1461_cadbbbdd from uid 1000 finished with success after 37508ms
 2/13/22 6:05 PM	PackageKit	search-file transaction /1462_cecbaeed from uid 1000 finished with success after 301ms
 2/13/22 6:05 PM	PackageKit	search-file transaction /1463_ecddabcc from uid 1000 finished with success after 294ms
 2/13/22 6:05 PM	PackageKit	search-file transaction /1464_aacbacca from uid 1000 finished with success after 291ms
 2/13/22 6:05 PM	systemd	tracker-extract-3.service: Deactivated successfully.
 2/13/22 6:05 PM	PackageKit	search-file transaction /1465_edacadce from uid 1000 finished with success after 294ms
 2/13/22 6:05 PM	PackageKit	get-details transaction /1466_cacdcdca from uid 1000 finished with success after 239ms

---

### Post by grahammechanical on 2022-02-14
Enter this command in a terminal and see the result:

```
tracker status
```

Apparently, systemd (a part of the OS) is indexing files in Documents, Music, Pictures, Videos, and Downloads folders.

[https://askubuntu.com/questions/1179780/tracker-service-running-every-minute](https://askubuntu.com/questions/1179780/tracker-service-running-every-minute)

See the third post on that link. An official Ubuntu package is running. It origin is from the Gnome developers.

[https://ubuntu.pkgs.org/20.04/ubuntu-main-arm64/tracker-extract_2.3.3-2_arm64.deb.html](https://ubuntu.pkgs.org/20.04/ubuntu-main-arm64/tracker-extract_2.3.3-2_arm64.deb.html)

[https://wiki.gnome.org/Projects/Tracker](https://wiki.gnome.org/Projects/Tracker)

Regards

---

### Post by mlempenau on 2022-02-15
Many thanks,  I have a synology server that was working but I upgraded to 21.10 and it's not updating and I've been too busy to figure out why.  That is probably what started systemd to begin with.  What worried me was I saw tracker and miner and was worried that something bad had started tracking me.  The result of tracker status was:
mlempenau@michael-21:~$ tracker status
Command 'tracker' not found, but can be installed with:
sudo apt install tracker

If I had a bad tracker using my s/w would "tracker status" let me know this?   Thanks again.

---

### Post by MAFoElffen on 2022-02-15
[GNOME Tracker]("https://gnome.pages.gitlab.gnome.org/tracker/faq/"). <<-- That is the FAQ. It indexes content from your home directory automatically, so that applications can provide instant search results when you need them. If, in it's settings, the verbosity is set to "errors" on dconf database you shouldn't see anything on journalctl.

Or you can disable it via:
```

systemctl --user mask tracker-store.service tracker-miner-fs.service tracker-miner-rss.service tracker-extract.service tracker-miner-apps.service tracker-writeback.service 
tracker reset --hard
sudo reboot

```
BUT... since you just posted that your system is saying that 'tracker' is not found as a command, then this is a bit confusing... It is installed by default.
```

mafoelffen@Mikes-ThinkPad-T520:~$ which tracker
/usr/bin/tracker

mafoelffen@Mikes-ThinkPad-T520:~$ tracker status
Currently indexed: 261 files, 28 folders
Remaining space on database partition: 286.5 GB (29.14%)
All data miners are idle, indexing complete

mafoelffen@Mikes-ThinkPad-T520:~$ find /var/lib/systemd/deb-systemd-user-helper-enabled/ -name tracker*
/var/lib/systemd/deb-systemd-user-helper-enabled/tracker-miner-fs.service.dsh-also
/var/lib/systemd/deb-systemd-user-helper-enabled/tracker-extract.service.dsh-also
/var/lib/systemd/deb-systemd-user-helper-enabled/default.target.wants/tracker-extract.service
/var/lib/systemd/deb-systemd-user-helper-enabled/default.target.wants/tracker-miner-fs.service

mafoelffen@Mikes-ThinkPad-T520:~$ gsettings list-recursively | grep Tracker | grep verbosity
org.freedesktop.Tracker.Writeback verbosity 'errors'
org.freedesktop.Tracker.Extract verbosity 'errors'
org.freedesktop.Tracker.Store verbosity 'errors'
org.freedesktop.Tracker.Miner.Files verbosity 'errors'

```
But as seen by the FAQ above, it is not malicious. It should not need to be tweaked unless it is causing high CPU usage, which historically was fixed in 19.10, from happening all the time, to just checking once an hour... By the now default setting is not make entries in journalctl unless an 'error' with it, it just makes less entries in the journalctl than it used to (prior to 19.10), so that admins did't get distracted by them, when they thought that those messages were some kind of nuisance.

---

