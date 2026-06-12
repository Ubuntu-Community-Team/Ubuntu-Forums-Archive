---
title: "Ubuntu Installation tip needed"
date: 2007-05-29
forum: General Help
---

### Post by Chas on 2007-05-29
Hello, What am I missing here? - Thanks.

I would like to use my lynx browser.

lynx
bash: lynx: command not found

sudo aptitude install lynx
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
No candidate version found for lynx
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done


locate lynx
/etc/X11/config/cf/lynx.cf
/lib/modules/2.6.12-9-386/kernel/drivers/ieee1394/pcilynx.ko
/usr/share/doc/w3m/examples/keymap.lynx
/usr/share/doc/w3m/ja/examples/keymap.lynx
/usr/share/vim/vim63/syntax/lynx.vim
/usr/share/Terminal/apps/lynx.desktop


sudo aptitude search lynx
v   lynx                    


cat /etc/apt/sources.list

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe



Thanks for your help.
Chas.

---

### Post by Blender on 2007-05-29
Sorry, can't really help with the repo thing, don't know what's wrong with it (must be a problem there, though).

But you can download the package manually from [http://packages.ubuntu.com/breezy/web/lynx]("http://packages.ubuntu.com/breezy/web/lynx")
and install it with **dpkg**.

---

### Post by aysiu on 2007-05-29
Maybe you need to do update first? ```
sudo aptitude update
sudo aptitude install lynx
sudo updatedb
locate lynx
lynx
```

---

### Post by Chas on 2007-05-29
Hello,
Thank you for your help.
I would like to learn to use the command line.
I would also like to use aptitude rather than download the package manually .
I am presently using Xfce.
I have tried your advice.
Any ideas what to do next?

sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [191B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Sources
Fetched 2B in 1m3s (0B/s)
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done

sudo aptitude upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done


sudo aptitude install lynx
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
No candidate version found for lynx
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done

---

### Post by confused57 on 2007-05-29
Have you performed a search in Synaptic Package Manager to see if there is a lynx package listed?

I used Lynx web browser in a Linux From Scratch installation:
[http://www.linuxfromscratch.org/blfs/view/stable/basicnet/lynx.html](http://www.linuxfromscratch.org/blfs/view/stable/basicnet/lynx.html)

This is definitely installing from source, but it might give you some ideas...I deleted the LFS partition some time back and had Lynx working quite well.  The above installation may only work with LFS 6.2, but you might be able to find a .deb file or a google search may turn up something.

---

### Post by Chas on 2007-05-29
Hello, thanks.
I don't use synaptic.
I prefer the command prompt.
Aptitude seems to be a good choice.
Aptitude does a search too.
This is what I get.

sudo aptitude search lynx
v   lynx

I think I may not be linked up to all the repositories.
I think you link up to repositories through this file:

cat /etc/apt/sources.list

output in earlier above.

---

### Post by aysiu on 2007-05-29
Well, this looks like the problem: ```
Err http://us.archive.ubuntu.com breezy Release.gpg
Temporary failure resolving 'us.archive.ubuntu.com'
Err http://security.ubuntu.com breezy-security Release.gpg
Temporary failure resolving 'security.ubuntu.com'
``` Can you try using a different mirror?
This will help: [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by Chas on 2007-05-29
Hello, thanks.
I updated my  /etc/apt/sources.list
like you suggested, but as you see
the error is still there.
Any ideas how to get lynx and other common 
packages to install through aptitude?

cat /etc/apt/sources.list
# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/multiverse Packages
Fetched 1B in 1m2s (0B/s)
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done

sudo aptitude install lynx
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
No candidate version found for lynx
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done

---

### Post by aysiu on 2007-05-29
Well, you're still using the US mirror. The idea is to use source-o-matic to get a different mirror.

---

### Post by Chas on 2007-05-30
Hello, thanks for your input.
I tried another country.
It does not seem to matter.

sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Err [http://kh.archive.ubuntu.com](http://kh.archive.ubuntu.com) breezy Release.gpg
  Temporary failure resolving 'kh.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Get:1 [http://kh.archive.ubuntu.com](http://kh.archive.ubuntu.com) breezy-updates Release.gpg [191B]
Get:2 [http://kh.archive.ubuntu.com](http://kh.archive.ubuntu.com) breezy-updates Release [29.6kB]
Get:3 [http://kh.archive.ubuntu.com](http://kh.archive.ubuntu.com) breezy-updates/main Packages [59.5kB]
Get:4 [http://kh.archive.ubuntu.com](http://kh.archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Get:5 [http://kh.archive.ubuntu.com](http://kh.archive.ubuntu.com) breezy-updates/universe Packages [16.8kB]
Get:6 [http://kh.archive.ubuntu.com](http://kh.archive.ubuntu.com) breezy-updates/multiverse Packages [872B]
Fetched 107kB in 1m3s (1689B/s)
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done

Not only would I like to install lynx,
I would also like to install openoffice,
through the command line using aptitude.
Any hints on this?

sudo aptitude install openoffice
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Couldn't find any package matching "openoffice".  However, the following
packages contain "openoffice" in their description:
  language-pack-en-base language-pack-kde-af-base
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done

---

### Post by aysiu on 2007-05-30
Maybe [this](http://ubuntuforums.org/showthread.php?t=282042) might help.

---

### Post by Chas on 2007-05-30
Thanks for the pointer.
Had to sleep on it  - found this:

[http://ubuntuforums.org/showthread.php?p=1900192#post1900192](http://ubuntuforums.org/showthread.php?p=1900192#post1900192)

---

### Post by aysiu on 2007-05-30
> **Chas said:**
> Thanks for the pointer.
Had to sleep on it  - found this:

[http://ubuntuforums.org/showthread.php?p=1900192#post1900192](http://ubuntuforums.org/showthread.php?p=1900192#post1900192)
So did that fix the problem?

---

### Post by Chas on 2007-05-30
No, I thought I had the answer, but that wasn't it.  I did more searching around the forums, but to no avail.  Here is further info - this install is on a Sony Vaio pcg z505rx 400 mhx 192 ram 6 gb hd.

It's a server only install from a free breezy Ubuntu promo CD.  On top of the server install is xfce, which I installed after setting up my wireless card and using aptitude.  I've had this install for about one month on this laptop and it is the more "tweaked" than any other time.  Works pretty good for an old system.  Concerning internet connectivity, I have been browsing the web fine with Firefox for weeks - also using ftp and ssh.

So this is where I am stuck.
I have these errors:

sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Err [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) breezy-extras Release.gpg
  Temporary failure resolving 'ftp2.caliu.info'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [191B]

Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) ......... 
(removed for ease of reading)

Fetched 2B in 1m8s (0B/s)
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done

---

### Post by aysiu on 2007-05-30
I did a lot of searching too, and the best I could come up with was the link in post #11.

---

