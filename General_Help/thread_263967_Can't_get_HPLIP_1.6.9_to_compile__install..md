---
title: "Can't get HPLIP 1.6.9 to compile / install."
date: 2006-09-24
forum: General Help
---

### Post by Ziptar on 2006-09-24
I have spent a good portion of today trying to get my HP PSC 2510 Wirless All in One  working under Ubuntu.

After much forum reading I found that many HP AIOs aren't detected by the default HPLIP software in Ubuntu.

I have downloaded HPLIP 1.6.9 and am following the [installation instructions]("http://hplip.sourceforge.net/install/step3/index.html") However I can't get it to compile..

I do step # 7  "[COLOR="DarkGreen"]*./configure --prefix=/usr*[/COLOR]" it starts but ends with 

[COLOR="Blue"][I]"checking for usb_init in -lusb... no 
 configure: error: cannot find libusb support"[/I][/COLOR]

If I try to proceed on to the next steps it fails.

Step 14 *[COLOR="DarkGreen"]"sudo make install"[/COLOR]* gives me:
[COLOR="Blue"]*"make: *** No rule to make target `install'.  Stop."*[/COLOR]

If I try *[COLOR="DarkGreen"]"sudo checkinstall"[/COLOR]* I get:

[I][COLOR="Blue"]"true_fopen == 0 for fopen64("/proc/mounts", "r")
 make: *** No rule to make target `install'.  Stop.
 ****  Installation failed. Aborting package creation."[/COLOR][/I]

I am stuck at this point... I have downloaded the package several times and retried, I have been all over the forums and found similar issues but none of the fixes in other threads is working for me..

Is it me?? or is there a problem with HPLIP 1.6.9 ???

---

### Post by yopnono on 2006-09-24
Did you follow step 2.
[http://hplip.sourceforge.net/install/step2/ubuntu606.html](http://hplip.sourceforge.net/install/step2/ubuntu606.html)
```

sudo apt-get install build-essential python2.4-dev python2.4-qt3 libcupsys2-dev libsnmp9-dev libjpeg62-dev lsb libtool automake1.9 libusb-dev
```

---

### Post by Ziptar on 2006-09-24
Thanks, I thought I had....

```

Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
python2.4-qt3 is already the newest version.
libjpeg62-dev is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libcupsys2-dev: [COLOR="Red"]Depends: libcupsys2 (= 1.2.0-0ubuntu5) but 1.2.2-0ubuntu0.6.06  is to be installed
E: Broken packages[/COLOR]

```

so I uninstalled libcupsys2 in Synaptic and redid the apt-get and added libcupsys2.

```
~$ sudo apt-get install build-essential python2.4-dev pytho n2.4-qt3 [COLOR="Red"]libcupsys2 [/COLOR]libcupsys2-dev libsnmp9-dev libjpeg62-dev lsb libtool automa ke1.9 libusb-dev
```

Which gave me:
```
The following NEW packages will be installed:
  alien autoconf automake1.9 autotools-dev debconf-utils debhelper html2text
  libbeecrypt6 [COLOR="Red"]libcupsys2 [/COLOR]libcupsys2-dev libgcrypt11-dev libgnutls-dev
  libgpg-error-dev liblockfile1 libopencdk8-dev libpopt-dev librpm4
  libsnmp-perl libsnmp9-dev libssl-dev libtasn1-2-dev libtool libusb-dev
  libwrap0-dev lprng lsb lsb-core lsb-cxx lsb-desktop lsb-graphics m4 mailx
  ncurses-term pax postfix python2.4-dev rpm ssl-cert zlib1g-dev
```

the install seems to have proceeded normally except I got the same libcupsys2 pacakage for breezy again:

```
Get:14 http://us.archive.ubuntu.com dapper/main [COLOR="Red"]libcupsys2 1.2.0-0ubuntu5 [/COLOR][119kB ]


I then ran ./configure --prefix=/usr followed by sudo checkinstall everything seemed fine until checkinstall finished.

[CODE]dpkg: error processing /home/ziptar/Desktop/hplip-1.6.9/hplip-1.6.9_1.6.9-1_i386.deb (--install):
 trying to overwrite `/etc/sane.d/dll.conf', which is also in package libsane
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
```


Somehow in this process gedit was unintalled and when I try to reinstall it  synaptic tells me ```
gedit:
 Depends: libgnomeprint2.2-0 but it is not going to be installed
 Depends: libgnomeprintui2.2-0 but it is not going to be installed
 Depends: libgtksourceview1.0-0 but it is not going to be installed
  Depends: gedit-common (=2.14.2-0ubuntu3) but 2.14.4-0ubuntu1 is to be installed
```

Why am I having so many version issues??? Is the repository off?? How do I fix this?? just re-nstall Ubuntu and start over??

---

### Post by yopnono on 2006-09-24
Don't know. But did you do a clean install of dapper, or an dist-upgrade.
If an upgrade, you may have some repo from ubuntu.

Try to remove all dev packages an it's dependents. And try again.
Maybe some else know this better, I don't build stuff so much.

---

### Post by braddcadd on 2006-12-22
I am having the same problem:
```
sudo apt-get install -f libcupsys2-dev
```

yields:
```

The following packages have unmet dependencies:
  libcupsys2-dev: Depends: libcupsys2 (= 1.2.0-0ubuntu5) but 1.2.2-0ubuntu0.6.06 is to be installed
E: Broken packages

```

Any ideas?

---

### Post by braddcadd on 2006-12-25
Bump :)

---

### Post by braddcadd on 2007-01-01
Well I made a little progress for those interested.  I installed the problematic package with a force by selecting the second solution (downgrade the version of several packages):
```
sudo aptitude install -f libcupsys2-dev
```

The HPLIP instructions worked for me.  Altough now I am having trouble with sane.  Oh well, on to the next post/problem ( [http://www.ubuntuforums.org/showthread.php?p=1955557#post1955557](http://www.ubuntuforums.org/showthread.php?p=1955557#post1955557) ).

Hope that helps...

---

### Post by moshuptrail on 2007-01-01
I just went to 1.6.12 - which they claim they have tested on Dapper.  I installed that one the other day and it automatically brought in all the dependencies.  I also had to upgrade libusb to 0.1.8 or something like that.

Anyway, it's available on the hplip site:
[http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)

---

