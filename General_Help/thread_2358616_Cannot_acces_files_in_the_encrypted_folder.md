---
title: "Cannot acces files in the encrypted folder"
date: 2017-04-15
forum: General Help
---

### Post by Canaryguy on 2017-04-15
Hello,

I have installed Ubuntu 17.04 and Ubuntu Gnome 17.04. Both of them have the home directory encrypted.
I'd like to access from one system the home directory from the other unmounted system.
I have the passphrase of both operating systems.

For example:
From Ubuntu I mount the partition where Ubuntu Gnome is (simply clicking on the icon on the Unity left bar)
From Terminal: [B]sudo ecryptfs-recover-private /media/"user"/
[/B]
At the end it seems that everything has worked fine. The command line tells me that the data are now in /tmp/"decrypted directory" but when I open this folder I cannot see my files. Either there's nothing there or I see the file **"Access-Your-Private-Data.desktop"** and[B] "README.txt"
[/B]
Does anybody know what the problem is?

---

### Post by #&amp;thj^% on 2017-04-15
Huumm? Not sure I can help here>> but what dose this return from the terminal:
```
cd /tmp
ls -go
```

---

### Post by Canaryguy on 2017-04-15
This is what I get when I run the command ls -go
total 36
-rw-------  1    0 Apr 15 18:56 config-err-e0Xg6V
drwxr-x---+ 3 4096 Apr 15 18:59 ecryptfs.mlaqRsBy
drwx------  2 4096 Apr 15 18:57 firefox_marcos
drwx------  2 4096 Apr 15 18:56 ssh-KrVjaWKgMkhj
drwx------  3 4096 Apr 15 18:45 systemd-private-059696c7595241458a5b38d3c50b7da6-colord.service-fpoKyq
drwx------  3 4096 Apr 15 18:57 systemd-private-059696c7595241458a5b38d3c50b7da6-fwupd.service-NwgnoJ
drwx------  3 4096 Apr 15 18:44 systemd-private-059696c7595241458a5b38d3c50b7da6-iio-sensor-proxy.service-Q08Jz4
drwx------  3 4096 Apr 15 18:45 systemd-private-059696c7595241458a5b38d3c50b7da6-rtkit-daemon.service-jIVmKO
drwx------  3 4096 Apr 15 18:44 systemd-private-059696c7595241458a5b38d3c50b7da6-systemd-resolved.service-YUpf3F
drwx------  3 4096 Apr 15 18:44 systemd-private-059696c7595241458a5b38d3c50b7da6-systemd-timesyncd.service-dRudYn
-rw-rw-r--  1    0 Apr 15 18:56 unity_support_test.0

Supposedly I have the data in "ecryptfs.mlaqRsBy" but inside this folder there's only another folder that contains nothing, not even hidden files.

---

### Post by #&amp;thj^% on 2017-04-15
> **Canaryguy said:**
> This is what I get when I run the command ls -go
total 36
_**-rw-------  1    0 Apr 15 18:56 config-err-e0Xg6V**_

Supposedly I have the data in "ecryptfs.mlaqRsBy" but inside this folder there's only another folder that contains nothing, not even hidden files.

I think this might be your problem....I Need to think some on this before offering any other advice.

---

### Post by #&amp;thj^% on 2017-04-15
BTW is this a upgrade to 17.04? or a fresh clean install..

---

### Post by Canaryguy on 2017-04-15
It's a clean installation. A partition for Ubuntu and another for Ubuntu Gnome.

---

