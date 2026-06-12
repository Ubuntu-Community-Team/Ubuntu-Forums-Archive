---
title: "error installing filezilla"
date: 2012-11-09
forum: General Help
---

### Post by qwertyjjj on 2012-11-09
j-media-centre@jmediacentre-A880G:~$ sudo apt-get install filezilla
[sudo] password for j-media-centre: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 filezilla : Depends: filezilla-common (= 3.5.3-1ubuntu2) but 3.5.3-oneiric~ppa1 is to be installed
E: Unable to correct problems, you have held broken packages.


Any ideas on how to solve that?

---

### Post by hwttdz on 2012-11-09
First make sure you run update & upgrade, then I'd try removing filezilla-common and then installing filezilla and maybe it will get the versioning right.  Let us know if that doesn't work.

---

### Post by qwertyjjj on 2012-11-22
> **hwttdz said:**
> First make sure you run update & upgrade, then I'd try removing filezilla-common and then installing filezilla and maybe it will get the versioning right.  Let us know if that doesn't work.

j-media-centre@jmediacentre-A880G:~$ sudo apt-get upgrade
[sudo] password for j-media-centre: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up transmission-daemon (2.72-0ubuntu0.12.04.1) ...
 * Starting bittorrent daemon transmission-daemon                               [19:22:06.218] JSON parser failed in /var/lib/transmission-daemon/info/settings.json at line 46, column 17: "“password”,
"
invoke-rc.d: initscript transmission-daemon, action "start" failed.
dpkg: error processing transmission-daemon (--configure):
 subprocess installed post-installation script returned error exit status 255
Errors were encountered while processing:
 transmission-daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)
j-media-centre@jmediacentre-A880G:~$

---

### Post by hwttdz on 2012-11-22
That's odd in that it's an error with a different package.  Now I'd suggest reinstalling the transmission packages (any of "transmission transmission-common transmission-dbg transmission-qt transmission-cli transmission-daemon transmission-gtk transmission-remote-cli" that you have installed), and maybe "sudo apt-get -f install".

---

