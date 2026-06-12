---
title: "Help! apt and dpkg broken"
date: 2007-01-05
forum: General Help
---

### Post by dragon76 on 2007-01-05
I have a big problem apt-get, dpkg, and synaptic have all been rendered useless on my system due to installing and attempting to remove gpar2. I can no longer install, remove or update anything. See my thread:

[http://www.ubuntuforums.org/showthread.php?t=330967]("http://www.ubuntuforums.org/showthread.php?t=330967")

Please help as I haven't recieved any replies on this and I need to get it fixed soon.

I don't know if I need to somehow for apt to reset itself or what, but I need to test two new tuner cards that just arrived and can't. Not to mention there are security updates that I can't install.

Thanks

---

### Post by Mithrilhall on 2007-01-05
Do the following and post the output you get.

```

sudo apt-get update

```

---

### Post by dragon76 on 2007-01-05
update works ok, but here is the output:

Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US
Get:5 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Sources
Fetched 5B in 1s (5B/s)
Reading package lists... Done

---

### Post by Mithrilhall on 2007-01-05
Try this..

```
sudo dpkg --configure -a
```


Then try installing something

```
sudo apt-get install lynx
```

---

### Post by dragon76 on 2007-01-05
I still get the following error:

#apt-get install mplayer-doc
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package gpar2 needs to be reinstalled, but I can't find an archive for it.

---

### Post by Mithrilhall on 2007-01-05
Post a copy of your sources.list.

---

### Post by dragon76 on 2007-01-05
sources.list is attatched

---

### Post by dragon76 on 2007-01-05
try this again

---

### Post by Mithrilhall on 2007-01-05
I didn't find anything on gpar2 but I found this on gpar...

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=edgy&release=all&keywords=gpar&sourceid=mozilla-search](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=edgy&release=all&keywords=gpar&sourceid=mozilla-search)


For gpar2...have you tried installing via the deb file?
[http://packages.debian.org/unstable/utils/gpar2](http://packages.debian.org/unstable/utils/gpar2)

---

### Post by dragon76 on 2007-01-05
Yes that is where I got the deb file it was the previous version though

gpar2_0.3-1_i386.deb

btw - thanks so much for your help

---

### Post by dragon76 on 2007-01-05
Problem fixed by following the thread:

[http://www.ubuntuforums.org/showthread.php?t=308544]("http://www.ubuntuforums.org/showthread.php?t=308544")

I thought that the solution would be something similar to this but didn't know which files to edit.

Thanks for all the help Mithrilhall.

---

