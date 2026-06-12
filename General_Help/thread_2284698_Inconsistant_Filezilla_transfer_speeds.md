---
title: "Inconsistant Filezilla transfer speeds"
date: 2015-07-01
forum: General Help
---

### Post by k0tt0n on 2015-07-01
I'm using filezilla to transfer files over sftp from my seedbox. When I transfer multiple files some of them transfer at ridiculously slow speeds, like 8kb/sec. when the faster downloads finish, the slow ones stay slow. I've tried allowing different numbers of simultaneous downloads, from 2 to 10, but it makes no difference. If I stop the transfers and restart them, most of the time the slow transfers pickup speed to what they should be. It's really inconsistent and annoying. I have no idea how to use a command line ftp program and as a new Linux user I need a GUI.
Any suggestions would be appreciated.

---

### Post by Vladlenin5000 on 2015-07-01
Is it only the FTP transfers that are inconsistent?
Wired or wireless?

---

### Post by k0tt0n on 2015-07-01
> **Vladlenin5000 said:**
> Is it only the FTP transfers that are inconsistent?
Wired or wireless?

yes just the FTP transfers. I just added 1 file to download and it was only going at 8kb/sec. I had to stop and restart the queue several times and eventually it started faster and downloaded at the speed it should, around 650kb/sec. When I do speed tests etc the connection is consistent. It's wireless from my laptop. I did have a dual boot with Windows 8 and ran a program called CuteFTP which never had issues and consistently maxed out my connection speed. It's just Filezilla on Ubuntu.

---

