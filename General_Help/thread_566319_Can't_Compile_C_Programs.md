---
title: "Can't Compile C Programs"
date: 2007-10-03
forum: General Help
---

### Post by Ziad87 on 2007-10-03
Hello, this is my first post here, so I hope that this thread is in the correct place.

 First of all, please bear in mind that this is the first time I use any kind of Linux distribution. I am having problems compiling C programs. Whenever I enter "gcc filename.c" in the terminal. I receive the error "stdio.h: No such file or directory" in addition to other compile errors. By the way, I am using Ubuntu 7.04. 

 After searching through these forums and using Google, I found that many Ubuntu users suggested running the "sudo apt-get install build-essential" and the "sudo aptitude install build-essential" commands. Unfortunately, both of them did not work. Do these commands require an Internet connection? 

 At home I currently have a PPPOE connection and I tried the "sudo ppoeconf" but was not able to set up the connection properly. In addition, at my university I can only get an Internet connection through an automatic proxy configuration and I could not access the add/remove programs although I was able to access web pages.

 So is it possible to download the gcc packages (preferably pre-compiled binaries) from another computer and then copy/install them to Ubuntu? Also, what is the best IDE for C programming? 

Thank you.

---

### Post by Seisen on 2007-10-03
You should be able to pull build-essential off of the Ubuntu cd.

---

### Post by Rui Pais on 2007-10-03
> **Seisen said:**
> You should be able to pull build-essential off of the Ubuntu cd.

yes. btw it can be done with just a command line:
```
sudo apt-cdrom add
```
:)

---

### Post by Ziad87 on 2007-10-03
Thanks a lot. Now I can successfully compile C programs. One more thing can you please recommend the best ide for C programming (preferably one that is already pre-compiled to work with Ubuntu)?

Thank you.

---

### Post by tekkenlord on 2007-10-03
perhaps you would like to try anjuta or kdevelop.

---

### Post by Rui Pais on 2007-10-03
Or Code::Blocks. 
It's simpler then Anjuta or kdevelop. 
It's not on repos, but there are builds for Ubuntu all flavors. [Here the latest version.]("http://forums.codeblocks.org/index.php?topic=6985.0")

[How it works here]("http://forums.codeblocks.org/index.php/topic,3232.0.html").

---

### Post by Ziad87 on 2007-10-03
Rui Pais, sorry for my constant questions. Since I am downloading the packages from another computer, which one of the packages on [http://lgp203.free.fr/pool/codeblocks/](http://lgp203.free.fr/pool/codeblocks/) should I choose? I have a 386 Intel.

Thanks.

---

### Post by Rui Pais on 2007-10-03
> **Ziad87 said:**
> Rui Pais, sorry for my constant questions. Since I am downloading the packages from another computer, which one of the packages on [http://lgp203.free.fr/pool/codeblocks/](http://lgp203.free.fr/pool/codeblocks/) should I choose? I have a 386 Intel.

Thanks.

No problem with questions :)

Installing codeblocks offline could be hard. The problem is that you need to upgrade the ubuntu version of wxwidgets. Thats just a step with an internet connection, but without it...
I can give instructions, but you need to manually download 8 packages from 2 different sites and install them by hand. 

Another alternative is using an older version of Code::blocks. Any version prior to 9 June of 2006 will work with Feisty wxwidgets ([here is a chronological list of binaries]("http://forums.codeblocks.org/index.php/board,20.0.html")). 

Another nice and very light "IDE" (almost an editor+console+color syntax) is geany.
You may prefer try it first. You can get the Ubuntu official or the latest from [here]("http://www.getdeb.net/search.php?keywords=geany").

If you still interested on Code::blocks i can post a list of packages needed and the links for the sites where they can be downloaded.

---

### Post by Ziad87 on 2007-10-05
Rui Pais, can you please list the binaries in chronological order for the latest version of Code::blocks? Today I tried updating Ubuntu using every possible way (ethernet, wireless, and even modem) and none of them were successful. So I manually downloaded and installed Emacs only to find out that it is far from an ideal ide for programming (its basically a text editor).

Thank you.

---

### Post by Rui Pais on 2007-10-08
> **Ziad87 said:**
> Rui Pais, can you please list the binaries in chronological order for the latest version of Code::blocks? Today I tried updating Ubuntu using every possible way (ethernet, wireless, and even modem) and none of them were successful. 
Sorry the late answer, i've been out of town...

ok, go here:
[http://apt.wxwidgets.org/dists/feisty-wx/main/binary-i386/](http://apt.wxwidgets.org/dists/feisty-wx/main/binary-i386/)
and download the 2.8.4 debs of:
[B] libwxgtk2.8-0 
 libwxgtk2.8-dev 
 libwxbase2.8-0
 libwxbase2.8-dev
 wx2.8-headers 
 wx-common[/B]

You can get them by copy+paste this:```

wget http://apt.wxwidgets.org/dists/feisty-wx/main/binary-i386/libwxgtk2.8-0_2.8.4.2-0_i386.deb http://apt.wxwidgets.org/dists/feisty-wx/main/binary-i386/libwxgtk2.8-dev_2.8.4.2-0_i386.deb http://apt.wxwidgets.org/dists/feisty-wx/main/binary-i386/libwxbase2.8-0_2.8.4.2-0_i386.deb http://apt.wxwidgets.org/dists/feisty-wx/main/binary-i386/libwxbase2.8-dev_2.8.4.2-0_i386.deb http://apt.wxwidgets.org/dists/feisty-wx/main/binary-i386/wx2.8-headers_2.8.4.2-0_i386.deb http://apt.wxwidgets.org/dists/feisty-wx/main/binary-i386/wx-common_2.8.4.2-0_i386.deb
```

If you want you can install the latest 2.8.6 (it seems to work alright, but don't know if problems couldn't arise)
```
wget http://apt.wxwidgets.org/dists/feisty-wx/main/binary-i386/libwxgtk2.8-0_2.8.6.0-0_i386.deb http://apt.wxwidgets.org/dists/feisty-wx/main/binary-i386/libwxgtk2.8-dev_2.8.6.0-0_i386.deb http://apt.wxwidgets.org/dists/feisty-wx/main/binary-i386/libwxbase2.8-0_2.8.6.0-0_i386.deb http://apt.wxwidgets.org/dists/feisty-wx/main/binary-i386/libwxbase2.8-dev_2.8.6.0-0_i386.deb http://apt.wxwidgets.org/dists/feisty-wx/main/binary-i386/wx2.8-headers_2.8.6.0-0_i386.deb  http://apt.wxwidgets.org/dists/feisty-wx/main/binary-i386/wx-common_2.8.6.0-0_i386.deb
```
and install it with:
```
sudo dpkg -i libwxgtk2.8-* wx-common* wx2.8-headers*
```
Set them the default (should be done it by installation, but, just in case):
```
sudo update-alternatives --config wx-config
```

The latest official nightly build for Linux is here:
[http://prdownload.berlios.de/codeblocks/CB_20070916_rev4472_Ubuntu6.10+7.04_wx2.8.4.tar.gz](http://prdownload.berlios.de/codeblocks/CB_20070916_rev4472_Ubuntu6.10+7.04_wx2.8.4.tar.gz)
Decompress it and inside there are several debs. They are all need.

An _alternative_ for that are user made (from pasgui) slightly more updated:
[http://lgp203.free.fr/pool/codeblocks/](http://lgp203.free.fr/pool/codeblocks/)
you'll need the latest versions of:
[B] libcodeblocks0
 codeblocks 
 libwxsmithlib0 
 codeblocks-contrib[/B]

hth

> So I manually downloaded and installed Emacs only to find out that it is far from an ideal ide for programming (its basically a text editor).

well emacs is much more then that... but i agree it's very hard to use and requiring a huge learning curve.

---

