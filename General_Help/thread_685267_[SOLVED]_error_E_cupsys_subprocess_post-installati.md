---
title: "[SOLVED] error E: cupsys: subprocess post-installation script returned error exit sta"
date: 2008-02-02
forum: General Help
---

### Post by cybergalvez on 2008-02-02
I get this error:
E: cupsys: subprocess post-installation script returned error exit status 1
every time I install or update anything with apt-get or synatic.  Does anyone know what I can do to fix the error?
Jose

---

### Post by dcstar on 2008-02-02
> **cybergalvez said:**
> I get this error:
E: cupsys: subprocess post-installation script returned error exit status 1
every time I install or update anything with apt-get or synatic.  Does anyone know what I can do to fix the error?
Jose

Tell us the rest of the messages that appear.

---

### Post by cybergalvez on 2008-02-02
ok this is the typical error I get when I try to install anything, this time nmap:

```

sudo apt-get install nmap
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nmap
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/763kB of archives.
After unpacking 2724kB of additional disk space will be used.
Selecting previously deselected package nmap.
(Reading database ... 143741 files and directories currently installed.)
Unpacking nmap (from .../archives/nmap_4.20-2_amd64.deb) ...
Setting up cupsys (1.3.2-1ubuntu7.5) ...
Reloading AppArmor profiles : done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
Setting up nmap (4.20-2) ...

Errors were encountered while processing:
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Jose

---

### Post by cybergalvez on 2008-02-03
Anyone have any advice on how to fix this?
Jose

> **cybergalvez said:**
> ok this is the typical error I get when I try to install anything, this time nmap:

```

sudo apt-get install nmap
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nmap
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/763kB of archives.
After unpacking 2724kB of additional disk space will be used.
Selecting previously deselected package nmap.
(Reading database ... 143741 files and directories currently installed.)
Unpacking nmap (from .../archives/nmap_4.20-2_amd64.deb) ...
Setting up cupsys (1.3.2-1ubuntu7.5) ...
Reloading AppArmor profiles : done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
Setting up nmap (4.20-2) ...

Errors were encountered while processing:
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Jose

---

### Post by cybergalvez on 2008-02-06
Solved see this post for the solution [http://ubuntuforums.org/showthread.php?t=689046](http://ubuntuforums.org/showthread.php?t=689046)

---

