---
title: "&quot;The program 'docker' is currently not installed&quot;, even though I just installed it"
date: 2019-10-09
forum: General Help
---

### Post by pikku-pikkunen on 2019-10-09
I've tried installing the program docker both with muon and "apt-get install". However, when I try running it, the following error appears:

```
The program 'docker' is currently not installed. You can install it by typing:
sudo apt-get install docker
```

It still appears after following the instructions and running "sudo apt-get install docker". I have tried removing the program with both "apt-get remove" and "apt-get autoremove" and re-installing but without results.

What am I doing wrong?

---

### Post by sdsurfer on 2019-10-09
May not be all that helpful, just to confirm, you did the install as root with sudo? Attempting to run as root? (Their docs show you ways you don't have to run as root every time, once you get it running.) Missed something here?

[https://docs.docker.com/install/linux/docker-ce/ubuntu/](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

---

### Post by Tadaen_Sylvermane on 2019-10-09
I think you want docker.io, not just docker. Results of apt search below. I had a similar problem when doing a chroot installation of bionic with netplan / netplan.io

```
docker.io/bionic-updates,bionic-security 18.09.7-0ubuntu1~18.04.4 amd64
 Linux container runtime
```

```
docker/bionic 1.5-1build1 amd64
System tray for KDE3/GNOME2 docklet applications
```

---

