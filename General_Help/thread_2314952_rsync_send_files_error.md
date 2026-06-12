---
title: "rsync send_files error"
date: 2016-02-25
forum: General Help
---

### Post by brm on 2016-02-25
```

rsync: send_files failed to open "/home/bruce/colleen/COLLEEN-TOSHIBA/Colleen-T/Application Data/vlc/vlc-qt-interface.ini": Input/output error (5)
rsync: send_files failed to open "/home/bruce/colleen/COLLEEN-TOSHIBA/Colleen-T/Application Data/vlc/vlcrc": Input/output error (5)

sent 73,545 bytes  received 3,883 bytes  6,732.87 bytes/sec
total size is 1,415,643,703  speedup is 18,283.36
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1183) [sender=3.1.1]

```

rsync files to transfer some files from a Windows machine accessed through Samba to a backup directory on the Ubuntu host. The failed source files (and the target) all have the same permissions as hundreds of other files suuccessfully transferred. I have checked for problems with both filesystems; there are none. The source files are not zero-length.

I have Googled. Many have asked the question. There appears to be no answer so far.

---

### Post by mcgess on 2016-02-25
Hi

Are you able to open/copy either of these files using another command (or gui)?
Are you able to view the contents of the source files, I think they should be text?
I'm just wondering if they might be locked or corrupt.

Martin

---

