---
title: "no .avi or bumps, or flash"
date: 2007-08-23
forum: General Help
---

### Post by Devile on 2007-08-23
matt@matt-laptop:~/Desktop$ /home/matt/Desktop/bumps2.0/bumps

Codename: dapper
cp: cannot stat `channels.dapper': No such file or directory
--02:57:54--  [http://mirror.ubuntulinux.nl/1135D466.gpg](http://mirror.ubuntulinux.nl/1135D466.gpg)
           => `-'
Resolving mirror.ubuntulinux.nl... 88.198.22.52
Connecting to mirror.ubuntulinux.nl|88.198.22.52|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 755 [application/octet-stream]

100%[====================================>] 755           --.--K/s

02:57:54 (102.86 MB/s) - `-' saved [755/755]

OK
Reading package lists...
Building dependency tree...
Reading extended state information...
Initializing package states...
Building tag database...
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Ign [http://www.politicalcrossfire.com](http://www.politicalcrossfire.com) dapper Release.gpg
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates Release
Get:3 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas Release.gpg [307B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://www.politicalcrossfire.com](http://www.politicalcrossfire.com) dapper Release
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/universe Packages
Hit [http://www.politicalcrossfire.com](http://www.politicalcrossfire.com) dapper/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/universe Packages
Get:7 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas Release [23.7kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Get:8 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas/all Packages [19.9kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Fetched 43.9kB in 1s (29.5kB/s)
Reading package lists...
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
Reading package lists...
Building dependency tree...
bumps-multimedia is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 0B of additional disk space will be used.
Setting up flashplugin-nonfree (9.0.21.78~ubuntu1~dapper1) ...
Downloading... download failed
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of bumps-multimedia:
 bumps-multimedia depends on flashplugin-nonfree; however:
  Package flashplugin-nonfree is not configured yet.
dpkg: error processing bumps-multimedia (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 flashplugin-nonfree
 bumps-multimedia
E: Sub-process /usr/bin/dpkg returned an error code (1)
sudo died with exit status 100
matt@matt-laptop:~/Desktop$


that's my problem...  please help!

I CAN"T INSTALL ANYHING, not even my display drivers beucase of this stupid flash thing!

---

### Post by Sef on 2007-08-23
Are you using Ubuntu Dapper?  If not, what are you using?

---

### Post by Devile on 2007-08-23
it's ubuntu...

---

