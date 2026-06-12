---
title: "error when making a tgz package.."
date: 2008-06-19
forum: General Help
---

### Post by Mia_tech on 2008-06-19
I'm trying to make an .tgz pakage from ophcrack in my ubuntu box for a friend, and after decompressing the ophcrack source files, I do a ./configure and I get "configure: error: Cannot find ssl libraries"

any help appreciated

thanks

---

### Post by ad_267 on 2008-06-19
Have you installed the libssl-dev package?

---

### Post by Mia_tech on 2008-06-19
> **ad_267 said:**
> Have you installed the libssl-dev package?

thanks for the help... yes I did installed them, but now it stops at:
```
checking for Qt4 version of qmake... configure: error:
		ophcrack requires Qt toolkit version 4.3 or later.
		Please disable the GUI via '--disable-gui',
		or see http://www.trolltech.com/ to obtain it.

```
I've installed anything that have something to do with qmake and QT4, but no luck

any help appreciated

thanks

---

### Post by sdennie on 2008-06-19
Try:

```

sudo apt-get build-dep ophcrack

```

---

### Post by Mia_tech on 2008-06-19
> **vor said:**
> Try:

```

sudo apt-get build-dep ophcrack

```

after using your code...I it ask me for the Ubuntu install cdrom, I insert it and keep on asking me for it... here's the output
```
jorge@ubuntu-box:~/ophcrack-3.0$ sudo apt-get build-dep ophcrack
[sudo] password for jorge: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  autotools-dev debhelper dpatch gettext html2text intltool-debian
  libatk1.0-dev libcairo2-dev libgtk2.0-dev libpango1.0-dev libpixman-1-dev
  libxcomposite-dev libxdamage-dev po-debconf x11proto-composite-dev
  x11proto-damage-dev
0 upgraded, 16 newly installed, 0 to remove and 6 not upgraded.
Need to get 0B/6921kB of archives.
After this operation, 23.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)'
in the drive '/cdrom/' and press enter

Media change: please insert the disc labeled
 'Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)'
in the drive '/cdrom/' and press enter

```

thanks in advance

---

### Post by sdennie on 2008-06-19
That's easy enough to fix.  Go to System->Administration->Software Sources and remove the Hardy CD as a source.  Then, before rerunning the "apt-get build-dep" do:

```

sudo apt-get update

```

---

### Post by Mia_tech on 2008-06-19
> **vor said:**
> That's easy enough to fix.  Go to System->Administration->Software Sources and remove the Hardy CD as a source.  Then, before rerunning the "apt-get build-dep" do:

```

sudo apt-get update

```

I just did that with no luck... I was able to installed from synaptic, but what I want to do is create a .tgz package in which I'm supposed to do "./configure-->make & checkinstall"

it keeps giving me error
```
	ophcrack requires Qt toolkit version 4.3 or later.
```

thanks

---

### Post by ad_267 on 2008-06-19
Do you have libqt4-dev?

That's version 4.3.4 so should be fine.

Remember you need the "-dev" packages for compiling.

---

### Post by Mia_tech on 2008-06-19
> **ad_267 said:**
> Do you have libqt4-dev?

That's version 4.3.4 so should be fine.

Remember you need the "-dev" packages for compiling.

yes I have that installed, but I'm still getting error... 
```
checking for qmake-qt4... /usr/bin/qmake-qt4
checking for qmake... /usr/bin/qmake
checking for Qt4 version of qmake... configure: error:
		ophcrack requires Qt toolkit version 4.3 or later.
		Please disable the GUI via '--disable-gui',
		or see http://www.trolltech.com/ to obtain it.

```

---

