---
title: "i do not have cd rom anymore"
date: 2020-05-27
forum: General Help
---

### Post by Hotchilli on 2020-05-27
i do not have cd rom anymore here is apt-get update result

amma@amma-Aspire-F5-571:~$ sudo apt-get update
[sudo] password for amma: 
Ign:1 cdrom://Ubuntu 19.04 _Disco Dingo_ - Release amd64 (20190416) disco InRelease
Err:2 cdrom://Ubuntu 19.04 _Disco Dingo_ - Release amd64 (20190416) disco Release
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Ign:4 [http://mirror.us-midwest-1.nexcess.net/ubuntu](http://mirror.us-midwest-1.nexcess.net/ubuntu) disco InRelease            
Ign:5 [https://deb.torproject.org/torproject.org](https://deb.torproject.org/torproject.org) disco InRelease
Ign:6 [http://mirror.us-midwest-1.nexcess.net/ubuntu](http://mirror.us-midwest-1.nexcess.net/ubuntu) disco-updates InRelease
Err:7 [https://deb.torproject.org/torproject.org](https://deb.torproject.org/torproject.org) disco Release
  404  Not Found [IP: 116.202.120.166 443]
Ign:8 [http://mirror.us-midwest-1.nexcess.net/ubuntu](http://mirror.us-midwest-1.nexcess.net/ubuntu) disco-backports InRelease
Ign:9 [http://mirror.us-midwest-1.nexcess.net/ubuntu](http://mirror.us-midwest-1.nexcess.net/ubuntu) disco-security InRelease
Err:10 [http://mirror.us-midwest-1.nexcess.net/ubuntu](http://mirror.us-midwest-1.nexcess.net/ubuntu) disco Release
  404  Not Found [IP: 208.69.120.125 80]
Err:11 [http://mirror.us-midwest-1.nexcess.net/ubuntu](http://mirror.us-midwest-1.nexcess.net/ubuntu) disco-updates Release
  404  Not Found [IP: 208.69.120.125 80]
Err:12 [http://mirror.us-midwest-1.nexcess.net/ubuntu](http://mirror.us-midwest-1.nexcess.net/ubuntu) disco-backports Release
  404  Not Found [IP: 208.69.120.125 80]
Err:13 [http://mirror.us-midwest-1.nexcess.net/ubuntu](http://mirror.us-midwest-1.nexcess.net/ubuntu) disco-security Release
  404  Not Found [IP: 208.69.120.125 80]
Reading package lists... Done
E: The repository 'cdrom://Ubuntu 19.04 _Disco Dingo_ - Release amd64 (20190416) disco Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'https://deb.torproject.org/torproject.org disco Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://mirror.us-midwest-1.nexcess.net/ubuntu disco Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://mirror.us-midwest-1.nexcess.net/ubuntu disco-updates Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://mirror.us-midwest-1.nexcess.net/ubuntu disco-backports Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://mirror.us-midwest-1.nexcess.net/ubuntu disco-security Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

---

### Post by SeijiSensei on 2020-05-27
Remove, or comment out with a leading hash mark ("#"), the CD-ROM entries in /etc/apt/sources.list.

Most of these problems come from the fact that 19.04 ("Disco Dingo") reached end of life in January and is no longer supported.  I suggest a fresh install of 20.04 which has five years of support. For the vast majority of users, the versions with long-term support like 18.04 or 20.04 are the ones to install.

---

### Post by Hotchilli on 2020-05-27
thanks was not aware of that as i was away from end of sept to middle march and the dvd was in a linux mag

---

