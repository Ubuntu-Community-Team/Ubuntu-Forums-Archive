---
title: "Problem when updating Synaptic"
date: 2005-11-01
forum: General Help
---

### Post by Ronbo on 2005-11-01
Whenever I start Synaptic I am getting this error:

[HTML]W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)[/HTML]

I have checked my sources.list file and all seems in order.  Any ideas where my problem is?  Any help would be greatly appreciated.

My sources.list was taken from [http://www.psychocats.net/linux/sources.php]("http://www.psychocats.net/linux/sources.php") and is as follows:

[HTML]## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu breezy universe
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse 
[/HTML]

But I had these same errors before I made the change also.

---

### Post by trash-can on 2005-11-01
Try from console/terminal:```
sudo apt-get update
```What is the output?

---

### Post by Ronbo on 2005-11-01
When I run apt-get update this is what I get, and it just sits there, frozen.


[HTML]Get:1 http://security.ubuntu.com breezy-security Release.gpg [189B]
Hit http://security.ubuntu.com breezy-security Release
Get:2 http://archive.ubuntu.com breezy Release.gpg [189B]
Hit http://archive.ubuntu.com breezy Release
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://archive.ubuntu.com breezy/multiverse Packages
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://archive.ubuntu.com breezy/multiverse Sources
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
99% [Connecting to us.archive.ubuntu.com (130.239.18.173)][/HTML]

To get out of this I have to hit Ctrl-C.

---

### Post by trash-can on 2005-11-01
It seems that there is problem connecting to us.archive.ubuntu.com, try different mirror, something that is geographically closer to you. Take a look at [https://wiki.ubuntu.com/Archive](https://wiki.ubuntu.com/Archive) and replace us.archive.ubuntu.com with appropriate mirror in sources.list file.

---

### Post by Ronbo on 2005-11-01
That was it, thanks for the help.  Kinda wierd though, I'm surprised I couldn't find other posts about this.  You saved me alot of aggravation.

---

### Post by aysiu on 2005-11-01
[QUOTE=Ronbo]
My sources.list was taken from [http://www.psychocats.net/linux/sources.php]("http://www.psychocats.net/linux/sources.php") [/QUOTE] Thanks for bringing that error to my attention. I've updated the sources in that link.

---

