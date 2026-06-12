---
title: "Unmount External HDD Before Shutdown"
date: 2016-08-06
forum: General Help
---

### Post by dannymichel on 2016-08-06
I'm trying to unmount my external HDD before shutdown with a serveice.
I tried testing the service but it didnt work
```
[unit]
description=Unmount storage drive on shutdown
Before=shutdown.target reboot.target halt.target

[Service]
type=oneshot
RemainAfterExit=true
ExecStart=/bin/true
ExecStop=/bin/sh umount /media/storage

[Install]
WantedBy=multi-user.target
```


```
Created symlink from /etc/systemd/system/multi-user.target.wants/unmount-storage.service to /etc/systemd/system/unmount-storage.service.
danny@danny:~$ cd /media/storage
danny@danny:/media/storage$ cd
danny@danny:~$ sudo systemctl start unmount-storage.service
danny@danny:~$ cd /media/storage
danny@danny:/media/storage$ ls -a
.          .HFS+ Private Directory Data?  ._.DS_Store               backup
..         .Spotlight-V100                ._netatalk-3.1.9.tar.bz2  data
.DS_Store  .Trashes                       .fseventsd                media
danny@danny:/media/storage$ 
```

---

### Post by Keith_Helms on 2016-08-06
Any particular reason you want to do this?  Once the system is shut down the external drive is technically not mounted.

---

### Post by dannymichel on 2016-08-07
I want to do this because if i dont stop plex, rtorrent, then unmount my drive manually, the next time i start the computer, the drive becomes read-only and i have to repair it to be able to write to it again.

---

