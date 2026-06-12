---
title: "apt-get help"
date: 2007-09-25
forum: General Help
---

### Post by mgummelt on 2007-09-25
I'm trying to install openoffice.org

I do:

apt-get install openoffice.org

I get:

Reading Package Lists... Done
Building Dependency Tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libice6: Depends: x11-common but it is not going to be installed
  libsm6: Depends: x11-common but it is not going to be installed
  libx11-6: Depends: xfree86-common (> 4.3.0) but it is not installable
  libxau6: Depends: x11-common but it is not going to be installed
  libxaw7: Depends: xfree86-common but it is not installable
  libxdmcp6: Depends: x11-common (>= 1:7.0.0) but it is not going to be installed
  libxext6: Depends: xfree86-common but it is not installable
  libxft1: Depends: xfree86-common but it is not installable
  libxi6: Depends: xfree86-common but it is not installable
  libxmu6: Depends: xfree86-common but it is not installable
  libxmuu1: Depends: xfree86-common but it is not installable
  libxp6: Depends: xfree86-common but it is not installable
  libxpm4: Depends: xfree86-common but it is not installable
  libxrandr2: Depends: xfree86-common but it is not installable
  libxt6: Depends: xfree86-common but it is not installable
  libxtrap6: Depends: xfree86-common but it is not installable
  libxtst6: Depends: xfree86-common but it is not installable
  openoffice.org: Depends: openoffice.org-core (= 2.0.4.dfsg.2-7etch2) but it is not going to be installed
                  Depends: openoffice.org-writer but it is not going to be installed
                  Depends: openoffice.org-calc but it is not going to be installed
                  Depends: openoffice.org-impress but it is not going to be installed
                  Depends: openoffice.org-draw but it is not going to be installed
                  Depends: openoffice.org-math but it is not going to be installed
                  Depends: openoffice.org-base but it is not going to be installed
                  Depends: openoffice.org-java-common but it is not going to be installed
  xlibs-data: Depends: xfree86-common but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

So I do:

apt-get -f install

And I get:

Reading Package Lists... Done
Building Dependency Tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libx11-6 libx11-data libxaw7 libxext6 libxi6 libxmu6 libxmuu1 libxp6 libxpm4 libxrandr2 libxt6 libxtrap6 libxtst6 x11-common xbitmaps xcursor-themes
  xlibs-data
The following packages will be REMOVED:
  libxft1 xlibs
The following NEW packages will be installed:
  libx11-data x11-common xbitmaps xcursor-themes
The following packages will be upgraded:
  libx11-6 libxaw7 libxext6 libxi6 libxmu6 libxmuu1 libxp6 libxpm4 libxrandr2 libxt6 libxtrap6 libxtst6 xlibs-data
13 upgraded, 4 newly installed, 2 to remove and 292 not upgraded.
5 not fully installed or removed.
Need to get 0B/2085kB of archives.
After unpacking 6832kB disk space will be freed.
Do you want to continue? [Y/n] Y
Preconfiguring packages ...
(Reading database ... 38726 files and directories currently installed.)
Unpacking x11-common (from .../x11-common_1%3a7.1.0-19_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/x11-common_1%3a7.1.0-19_i386.deb (--unpack):
 unable to install new version of `./usr/share/man/man5/Xsession.5.gz': No such file or directory
Preparing to replace xlibs-data 4.3.0.dfsg.1-14sarge1 (using .../xlibs-data_1%3a7.1.0-19_all.deb) ...
Unpacking replacement xlibs-data ...
dpkg: error processing /var/cache/apt/archives/xlibs-data_1%3a7.1.0-19_all.deb (--unpack):
 unable to install new version of `./usr/share/doc/xlibs-data/copyright': No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/x11-common_1%3a7.1.0-19_i386.deb
 /var/cache/apt/archives/xlibs-data_1%3a7.1.0-19_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any ideas?

---

### Post by SPr on 2007-09-25
never mind.

---

### Post by mgummelt on 2007-09-25
never mind?  Does anyone know a solution to this?

---

### Post by zvacet on 2007-09-25
Like it say,install all dependencies you need.

---

### Post by rsambuca on 2007-09-25
Which version of Ubuntu are you running?  
What repositories are you using?
Isn't OO installed already on your system?

---

### Post by Scroobytec on 2007-09-25
Hi I am new to the Ubuntu thing, but why not just use the ADD/REMOVE Programs thing nothing is easier, just tick a box or two click the button and wait for the system to download and install the required files. AND then BOB'S your AUNTY you have open office (unfortunately this will be 2.2 and not the 2.3 Dev version).

But I even managed to install from the direct download made from Open Office.org, but what a dance that was, I was never really sure if that was really all that successful - but it was not in my mind so that set up was scrapped and I did it the "SAFE AND EASY WAY" giving me the confidence to use the software install. May be it is a carry over from toooooo many years in the DARK using the see through pices in the wall !!!!!!

Hope you succeed.

---

### Post by mgummelt on 2007-09-25
I'm actually on a VPS host with limited OS packages installed, so it doesnt have OO installed.

if I try one of the dependencies like:

apt-get install x11-common

I get:

Reading Package Lists... Done
Building Dependency Tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libx11-6: Depends: xfree86-common (> 4.3.0) but it is not installable
  libxaw7: Depends: xfree86-common but it is not installable
  libxext6: Depends: xfree86-common but it is not installable
  libxft1: Depends: xfree86-common but it is not installable
  libxi6: Depends: xfree86-common but it is not installable
  libxmu6: Depends: xfree86-common but it is not installable
  libxmuu1: Depends: xfree86-common but it is not installable
  libxp6: Depends: xfree86-common but it is not installable
  libxpm4: Depends: xfree86-common but it is not installable
  libxrandr2: Depends: xfree86-common but it is not installable
  libxt6: Depends: xfree86-common but it is not installable
  libxtrap6: Depends: xfree86-common but it is not installable
  libxtst6: Depends: xfree86-common but it is not installable
  xlibs-data: Depends: xfree86-common but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I'm actually on debian 3.1, but the apt-get issue should be the same, so I was hoping I could get some help here.

---

### Post by zvacet on 2007-09-25
```
sudo apt-get install x11-common
```

---

### Post by rsambuca on 2007-09-25
Did you try doing what it told you to do?

apt-get -f install

Also, the debian forums are an excellent resource if you are using debian :)

Are you using etch, lenny, or sid?

EDIT:  Don't you love it when you are trying to help someone and they don't tell you until post #7 that they are using a different OS?!

---

### Post by mgummelt on 2007-09-25
Any reason why Debian vs Ubuntu should even matter with apt-get?

And yes, as I said in my first post, I did apt-get -f install and got the output listed above.  I'm using Sarge.

---

### Post by rsambuca on 2007-09-25
I think I saw the word 'etch' in one of your error messages.  It may be that you have mixed repos.  Post your sources.list.

---

### Post by mgummelt on 2007-09-25
sources.list:

# See sources.list(5) for more information, especialy
# Remember that you can only use http, ftp or file URIs
# CDROMs are managed through the apt-cdrom tool.
#deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) stable main contrib non-free
#deb [http://non-us.debian.org/debian-non-US](http://non-us.debian.org/debian-non-US) stable/non-US main contrib non-free
deb [http://ftp.freenet.de/debian](http://ftp.freenet.de/debian) stable main contrib non-free
deb [http://security.debian.org](http://security.debian.org) stable/updates main contrib non-free

# Uncomment if you want the apt-get source function to work
#deb-src [http://http.us.debian.org/debian](http://http.us.debian.org/debian) stable main contrib non-free
#deb-src [http://non-us.debian.org/debian-non-US](http://non-us.debian.org/debian-non-US) stable/non-US main contrib non-free

---

### Post by rsambuca on 2007-09-25
Usually the debian repositories have the word 'etch' 'sid' 'lenny' in them.  I am not sure what packages those are pulling.  My guess is that the oo you are trying to install is requiring versions of some depencies that are not available in sarge.

Have you considered using the newest stable version of debian - etch 4.0?

---

