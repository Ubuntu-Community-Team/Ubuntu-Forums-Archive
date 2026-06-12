---
title: "Screwed up the system xD"
date: 2008-03-14
forum: General Help
---

### Post by TidusBlade on 2008-03-14
Okay, I feel like a retard now but anyways: Im running Ubuntu Dapper on a server but I think I removed a few important files and know normal commands like ls return this:
```
ls: error while loading shared libraries: libselinux.so.1: cannot open shared object file: No such file or directory
```
But I got libselinux installed...
And when I try to install files it says this:
```

Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  console-tools: Depends: sysvinit (> 2.74) but it is not going to be installed
  coreutils: PreDepends: libselinux1 (>= 1.28) but it is not going to be installed
  dhcp3-client: Depends: dhcp3-common (= 3.0.3-6ubuntu7) but it is not going to be installed
  klogd: Depends: adduser but it is not going to be installed
  libpam-modules: Depends: libselinux1 (>= 1.28) but it is not going to be installed
  mdadm: Depends: udev (>= 0.79-0ubuntu22) but it is not going to be installed
  openssh-server: Depends: libselinux1 (>= 1.28) but it is not going to be installed
                  Depends: adduser (>= 3.9) but it is not going to be installed
                  Depends: openssh-client (= 1:4.2p1-7ubuntu3) but it is not going to be installed
  screen: Depends: passwd (>= 1:4.0.3-10) but it is not going to be installed
  sysklogd: Depends: adduser but it is not going to be installed
  xserver-xorg: Depends: xserver-xorg-core but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
And then I try apt-get -f install which returns this:
```

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  base-files dhcp3-common initscripts language-pack-en language-pack-en-base libfontenc1 libx11-6 libxau6 libxdmcp6
  libxext6 libxfont1 libxxf86vm1 login openssh-client openssh-server sysvinit xfonts-utils xserver-xorg-core
Suggested packages:
  ssh-askpass xbase-clients rssh
Recommended packages:
  language-support-en xkeyboard-config
The following packages will be REMOVED:
  pcmciautils pppoeconf
The following NEW packages will be installed:
  base-files dhcp3-common initscripts language-pack-en libfontenc1 libx11-6 libxau6 libxdmcp6 libxext6 libxfont1
  libxxf86vm1 login openssh-client sysvinit xfonts-utils xserver-xorg-core
The following packages will be upgraded:
  language-pack-en-base openssh-server
2 upgraded, 16 newly installed, 2 to remove and 47 not upgraded.
41 not fully installed or removed.
Need to get 742kB/20.6MB of archives.
After unpacking 30.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libselinux1 base-files bash initscripts sysvinit udev language-pack-en language-pack-en-base login passwd libfontenc1
  xfonts-utils xfonts-100dpi xfonts-75dpi libxau6 libxdmcp6 libxfont1 xserver-xorg-core adduser dhcp3-common libx11-6
  libxext6 libxxf86vm1 libgl1-mesa libglu1-mesa freeglut3 libglitz-glx1 openssh-server openssh-client
Install these packages without verification [y/N]? y
Get:1 http://de.archive.ubuntu.com dapper-updates/main openssh-server 1:4.2p1-7ubuntu3.2 [205kB]
Get:2 http://de.archive.ubuntu.com dapper-updates/main openssh-client 1:4.2p1-7ubuntu3.2 [537kB]
Fetched 742kB in 0s (2906kB/s)
E: Sub-process /usr/sbin/dpkg-preconfigure --apt || true returned an error code (100)
E: Failure running script /usr/sbin/dpkg-preconfigure --apt || true

```
I know a few important packages arent there anymore but is there a way to get them back or something?

Thanks to anyone who will reply will anything!

---

### Post by kesman on 2008-03-14
Your profile says you are using Gutsy Gibbon, but the apt repositories are for Dapper Drake, so that's probably the problem here.

---

### Post by TidusBlade on 2008-03-14
If you read the first line it says
[QUOTE=TidusBlade]Im running Ubuntu Dapper on a server[/QUOTE]
Sorry for the confusion, and thanks for the reply.

---

### Post by kesman on 2008-03-14
Oh sorry about that =D otherwise, I have no idea how to fix this. Have you tried
```

sudo apt-get install --reinstall libselinux1

```
?

---

### Post by TidusBlade on 2008-03-14
Hope but it tells me this:
```
Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
And then apt-get -f install returns the same thing from the first post :(

---

### Post by kesman on 2008-03-14
how about
```

sudo apt-get -f install libselinux1

```

---

### Post by TidusBlade on 2008-03-14
Returns the same thing :(
```
Reading package lists... Done
Building dependency tree... Done
libselinux1 is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  console-tools: Depends: sysvinit (> 2.74) but it is not going to be installed
  dhcp3-client: Depends: dhcp3-common (= 3.0.3-6ubuntu7) but it is not going to be installed
  klogd: Depends: adduser but it is not going to be installed
  mdadm: Depends: udev (>= 0.79-0ubuntu22) but it is not going to be installed
  openssh-server: Depends: adduser (>= 3.9) but it is not going to be installed
                  Depends: openssh-client (= 1:4.2p1-7ubuntu3) but it is not going to be installed
  screen: Depends: passwd (>= 1:4.0.3-10) but it is not going to be installed
  sysklogd: Depends: adduser but it is not going to be installed
  xserver-xorg: Depends: xserver-xorg-core but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
I think theres a problem with essential files missing? If so, are these essential files recoverable, rebuildable or can I take them from somewhere else, or is a reinstall required?

---

