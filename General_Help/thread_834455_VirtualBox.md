---
title: "VirtualBox"
date: 2008-06-19
forum: General Help
---

### Post by andyg227 on 2008-06-19
I am a new user and am runnining Ubuntu 8 in a VirtualBox window.  My difficulty is with installing the Guest Additions.

Below is an exerpt from the VirtualBox manual:

***[INDENT]3. Change to the directory where your CD-ROM drive is mounted and execute as root: sh ./VBoxLinuxAdditions.run[/INDENT]***


I cannot get the file to run successfully, so I suppose that I am not navigating to the image correctly.

Thanks in advance for any suggestions.

   Andy

---

### Post by sdennie on 2008-06-19
Try:

```

cd /media/cdrom
sudo sh VBoxLinuxAdditions.run

```

---

### Post by forestpixie on 2008-06-19
If the cdrom command fails try cdrom0 - for some reaason it mounted there for me.

---

