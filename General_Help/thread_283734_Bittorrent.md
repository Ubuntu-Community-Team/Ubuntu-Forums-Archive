---
title: "Bittorrent"
date: 2006-10-24
forum: General Help
---

### Post by Tambo on 2006-10-24
Hi

I am trying to install bittorrent but having a little trouble running it.

```

$ sudo apt-get install bittorrent
$ sudo apt-get install bittorrent-gui
$ bittorrent-gui
bash: bittorrent-gui: command not found
$ locate bittorrent-gui
/var/cache/apt/archives/bittorrent-gui_3.4.2-6ubuntu2_all.deb
/var/lib/dpkg/info/bittorrent-gui.postinst
/var/lib/dpkg/info/bittorrent-gui.prerm
/var/lib/dpkg/info/bittorrent-gui.list
/var/lib/dpkg/info/bittorrent-gui.postrm
/var/lib/dpkg/info/bittorrent-gui.md5sums
/usr/lib/mime/packages/bittorrent-gui
/usr/share/doc/bittorrent-gui
/usr/share/doc/bittorrent-gui/changelog.Debian.gz
/usr/share/doc/bittorrent-gui/copyright

```

So it seems like it has no problem installing but I can't get it running, if it has indeed installed properly.

Here is my /etc/apt/sources.list

```

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/plf dapper free non-free
deb-src http://packages.freecontrib.org/plf dapper free non-free                                               
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main

```

Any problems anyone can see?

-Tom

---

### Post by tronica on 2006-10-24
try

> gnome-btdownload

---

### Post by Tambo on 2006-10-24
OK, well that seems to work, suppose I'll just stick with that. Thanks

---

### Post by tronica on 2006-10-24
to add that to your apps menu do 


alt+F2 and type

> alacarte

and go down to Internet, and check bitorrent.

---

