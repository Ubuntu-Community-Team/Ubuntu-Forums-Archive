---
title: "How to determine exact source of pending package update?"
date: 2015-02-12
forum: General Help
---

### Post by fr33z0n3r on 2015-02-12
I was doing updates using the Software Updater app on 14.04, and I decided to remove an undesired app from the command line.

After that I ran "apt-get upgrade" and noticed a set of packages that are not being advertised in the GUI app.  I'm a bit suspicious as to the specific source of these package adverts. 


1) How do I identify exactly which source is offering them?  
2) And is there a specific reason why they aren't visible in Software Updater?
3) How can I compare the existing versions of these packages easily?

```
user@host:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  libprocps3 libsmbclient libthumbnailer0 libwbclient0 postfix procps
  python-samba python3-distupgrade qtdeclarative5-ubuntu-thumbnailer0.1
  samba-common samba-common-bin samba-libs smbclient thumbnailer-service
  ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk
16 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 7,129 kB/7,362 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue? [Y/n] 
```

---

### Post by ian-weisser on 2015-02-12
1 and 3) Try 'apt-cache policy'
```
$ apt-cache policy libprocps3
libprocps3:
  Installed: 1:3.3.9-1ubuntu5.2
  Candidate: 1:3.3.9-1ubuntu5.2
  Version table:
 *** 1:3.3.9-1ubuntu5.2 0
        500 http://mirrors.gigenet.com/ubuntuarchive/ utopic-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1:3.3.9-1ubuntu5 0
        500 http://mirrors.gigenet.com/ubuntuarchive/ utopic/main amd64 Packages
```


2) Most likely Phased Updates.
See [https://wiki.ubuntu.com/PhasedUpdates](https://wiki.ubuntu.com/PhasedUpdates)
> Push out stable release updates to expanding subsets of the userbase so  that serious regressions can be detected before updates are pushed to  everyone, and the process stopped. The aim is for regressions to affect a  smaller proportion of our userbase.
Software Updater uses Phased Updates. apt-get doesn't.

---

### Post by ajgreeny on 2015-02-12
This is exactly the sort of situation where synaptic comes into its own.

Open synaptic, search by name for those packages, and you can see exactly what version you have, if it's installed, and which version is offered.

Synaptic is the BEST package manager available, without a doubt, and I don't think it is bothered by phased updates but gives you all packages with updates available.

---

### Post by fr33z0n3r on 2015-02-12
Thanks Ian!  That was informative.

```
user@host:~$ apt-cache policy libsmbclient
libsmbclient:
  Installed: 2:4.1.6+dfsg-1ubuntu2.14.04.4
  Candidate: 2:4.1.6+dfsg-1ubuntu2.14.04.5
  Version table:
     2:4.1.6+dfsg-1ubuntu2.14.04.5 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main i386 Packages
 *** 2:4.1.6+dfsg-1ubuntu2.14.04.4 0
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main i386 Packages
        100 /var/lib/dpkg/status
     2:4.1.6+dfsg-1ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main i386 Packages


```


Now, the followup question I have is how does package management work for updates?  Will it _**ONLY**_ permit the _**same**_ source to provide an update? Or can any source provide a relevant update?

---

### Post by ian-weisser on 2015-02-12
Any source can provide an update.
For example, a PPA can replace (update) a package provided by Main or Updates or Security...if dpkg can determine a useful version number. 
That's why you shouldn't add untrustworthy sources.

Making sure sources are somehow 'appropriate' is not a task apt is equipped for. Decisions like that are the human's job.

---

### Post by fr33z0n3r on 2015-02-12
Glad I didn't assume to begin with.  Thanks!

---

