---
title: "Can't run apt-get update"
date: 2014-04-17
forum: General Help
---

### Post by Sean_Anderson on 2014-04-17
Every time I run sudo apt-get update
I get the following error messages:
W: Failed to fetch cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1)/dists/saucy/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1)/dists/saucy/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1)/dists/saucy/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1)/dists/saucy/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch [http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/saucy/main/binary-amd64/Packages](http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/saucy/main/binary-amd64/Packages)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/saucy/main/binary-i386/Packages](http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/saucy/main/binary-i386/Packages)  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Navneet_Kumar on 2014-04-17
Please edit your /etc/apt/sources.list file and add the default repositiries in it..........and comment if solved.......

---

### Post by sffvba[e0rt on 2014-04-17
Edit your repo's as shown here - [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) and then disable the CD-ROM as well as the PPA for Deluge.

Try updating again.

---

### Post by Sean_Anderson on 2014-04-17
Thanks for you help so far I've added the PPA's and removed the CD and I'm still getting the following errors:

W: Failed to fetch [http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/saucy/main/binary-amd64/Packages](http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/saucy/main/binary-amd64/Packages)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/saucy/main/binary-i386/Packages](http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/saucy/main/binary-i386/Packages)  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by plucky on 2014-04-17
Remove the PPA as it doesn't have a repository for Saucy

[http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/](http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/)

Good Luck

---

### Post by Sean_Anderson on 2014-04-17
> **plucky said:**
> Remove the PPA as it doesn't have a repository for Saucy

[http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/](http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/)

Good Luck
Thanks a lot, this appears to have done the trick. :D

---

