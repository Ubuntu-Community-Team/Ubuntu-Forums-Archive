---
title: "Please Help!  Major libgtk dev problem"
date: 2006-08-09
forum: General Help
---

### Post by mikesena on 2006-08-09
This thing is driving me nuts!

1)I am trying to develop in Anjuta with GTK.  I open a project and it thinks, eventually spitting out that gtk2.0 doesn't exist.
2)I then began my search on the internet.  After a long session of Googling, I found that gtk2.0-dev was required!
3)I try to install the package, it says that libpango-dev aint going to installed.  libpango-dev in turn blames the fault on libpang itself [-X .
4)I look at forcing libpango down a version and shock horror, everything is going to uninstall (pratically).  libpango is useful, apparantly
5)More Googling into libpango-dev.  I download [a Debian 1.12.3](http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fp%2Fpango1.0%2Flibpango1.0-dev_1.12.3-1%2Bb1_i386.deb&md5sum=774083758bfb3faacd4e1da2d76c1e60&arch=i386&type=main), which complains that libpango original isn't good enough ( :-x )
6)Returned to google and found out about some ['Universe'](http://www.ubuntu.com/ubuntu/components#head-83c417468ac62506377459c6915798cdb7a24ae2) in ubuntu that can be enabled ([my search](http://www.google.com.hk/search?q=enabling+universe+in+ubuntu&start=0&ie=utf-8&oe=utf-8&client=firefox&rls=org.mozilla:en-US:unofficial)) and apparantly fixed a guy with a similar problem ([see this site](https://launchpad.net/distros/ubuntu/+source/gtk+2.0/+bug/547))
7)Looked at a number of the top hits, finding no amazing lines to 'uncomment' that would bring happiness. (I don't think i did, here is the file itself):```
deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -
# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://hk.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://hk.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://hk.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://hk.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

deb http://wine.budgetdedicated.com/apt dapper main
```8)Went to these forums and, after finding nothing, posted.

Can someone please help me fix this problem!!  A number of applications want the GTK-dev and it would be REALLY GOOD to install it!


Sorry about my attitude, little bit tired ;)  Ubuntu is great really, and according to [a test i did](http://www.zegeniestudios.net/ldc/), it's the distro for me


Ty,
Mike

---

### Post by RAOF on 2006-08-09
I think I've got it, but that sources.list is **really** difficult to read.  Whoever wrote that sources.list generator really needs to make the output more human-readable.

Strip out all the deb-src lines, and comments, and you get this:
```

deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free

deb http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

deb http://wine.budgetdedicated.com/apt dapper main
```
Particularly, it seems that you don't have any dapper-updates repositories enabled.  This is probably where the problem lies, I think.

You should probably add the following lines to your sources.list, run **sudo aptitude update** (to refresh your package lists), and then try to install libgtk2.0-dev again.

```

deb http://hk.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

```

---

### Post by mikesena on 2006-08-09
wow, whatever those two lines i added did worked!  libpango installed and so did gtk-dev.  i also have 54mb of updates to also do :P

thankyou vm!

---

### Post by mons on 2006-08-16
Thanks Raof, you are a :KS 
(well maybe not a KDE star, but some sort of star anyway).

I have spent the best part of 2 days trying to find a way to get to the correct libpango.  I modified my sources.list according to you advice, and presto! Install is successfull.

=D> \\:D/ 

Mons

---

