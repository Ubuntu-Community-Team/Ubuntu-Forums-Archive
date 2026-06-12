---
title: "Help installing qcomicbook"
date: 2005-05-12
forum: General Help
---

### Post by Josh M on 2005-05-12
I am trying to install the qcomicbook. The deb package is available here. 

[http://linux.bydg.org/~yogin/](http://linux.bydg.org/~yogin/)

When I try to install the package I get the following error message:

```
josh@ubuntu:~$ sudo apt-get install qcomicbook
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  qcomicbook: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
              Depends: libqt3c102-mt (>= 3:3.3.4) but 3:3.3.3-7ubuntu3 is to be installed
E: Broken packages
```


As far as I can tell, there is no newer versions of libc6 and  libqt3c102-mt via apt. 

When I ./configure on the tar.gz I get an error saying that I do not have a a qt installation. The author's website says you need the qt library, and links to [http://www.trolltech.com/](http://www.trolltech.com/).

I downloaded tar.gz from [http://www.trolltech.com/download/qt/x11.html](http://www.trolltech.com/download/qt/x11.html) but this crashed after a lengthy compile/install. 

Can ayone shed some light on getting this program installed? I'm a Linux newb, please don't flame me too hard :)

---

### Post by DutchLau on 2005-05-12
Although I'm not acquainted with the Qcomicbook, perhaps you could get an older version that depends on the slightly older Ubuntu libc6 and libqt3c102-mt files. I've had this problem several times before, and mostly with very new software. See if you can download an older version of the software, this should fix your problem!

Good luck and let us know when you've fixed your problem,

DutchLau

---

### Post by raditzman on 2005-05-30
Hi :)

I did it this way:
 0 - upgraded the system:
>  sudo apt-get dist-upgrade 
 1 - put debian unstable repositories in /etc/apt/sources.list. I use this line:
 'deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) unstable main contrib non-free'
 2-update apt 
> sudo apt-get update
 3-install the failed dependencies (sudo apt-get install whatever)
 4-install the package (sudo dpkg -i qcomicbook-version.deb)
 5-remove debian repositories from sources.list again
 6-update apt back to normal (same as 2):)
 
 works fine for me :)

---

