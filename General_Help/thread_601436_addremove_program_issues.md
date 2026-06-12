---
title: "add/remove program issues"
date: 2007-11-03
forum: General Help
---

### Post by lord.toan on 2007-11-03
Alright, I've installed Kubuntu 7.10 recently, and I want to install Firefox.  First I tried installing it from the web page, to no avail (I'm a TOTAL noob to this T_T) so i went to add/remove programs because I know I saw it there.  I go in and Firefox is grayed out and I can't click it.  I don't know how to fix this problem and it's getting annoying because Konqueror doesn't suit my needs very well (I can't get it to do very much).  

Everything else is running perfectly except Amarok isn't cooperating with the mp3 upgrade but that's not bothering me right now.  I just want to get Firefox working.  Can anyone help me out?  And possibly put it into terms that won't make my head fall off and cause flesh eating rats to come out of my closet and eat the insides of my skull? Because I need my skull.... Thanks in advance. :]

---

### Post by lord.toan on 2007-11-03
It seems the problem goes deeper than I thought.  If I tell it to ./configure a source folder to make an install file, i get this:

(This is an attempt to install Pigdin)

> checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name...
configure: error: C compiler cannot create executables


This seems like a serious problem.....

---

### Post by Maestro23 on 2007-11-03
If you are trying to install from source, you must 1st **install build-essential.**

> sudo apt-get install build-essential

Also, Firefox is in the Repositories.

> sudo apt-get install firefox

Installing Software in Ubuntu:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (Other good info as well)

---

### Post by lord.toan on 2007-11-03
Ah.  I was in the process of figuring that out.  Sorry, I'm a complete noob to this stuff. T_T I looked at the installation guide for Wine and figured that out, and then installed the .exe version of Firefox through the Kubuntu's Live CD.  I've still got to figure out Pidgin and the Linux version of Firefox though.  I'll try this when I get on my computer, my daughter's here right now and I gotta keep an eye on her, so probably when she goes to sleep.  Thank you for the information.

---

### Post by lord.toan on 2007-11-03
Huh...

> Reading package lists... Done
Building dependency tree
Reading state information... Done
Package firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package firefox has no installation candidate


---

### Post by lord.toan on 2007-11-03
The only thing I've been able to successfully install so far is Wine.

I just tried BitTorrent and got:

> make: *** No rule to make target `install'.  Stop.

I think somethin's wrong with this thing... T_T

---

