---
title: "Ubuntu vs Debian.Are both same thing ?"
date: 2012-12-03
forum: General Help
---

### Post by honey_bee on 2012-12-03
hi,
        I want to know that does Ubuntu has drived from Debian? For example if some one know Red Hat Linux file and directory structure ,he can do same in Fedora,CentOS. For debian user if he use then Ubuntu then file architecture is same as Debian ?

thanks
honey.

---

### Post by andrew.46 on 2012-12-03
File and directory structure are common to most Linux distros, with perhaps some significant differences in implementation. Ubuntu itself is a *fork* of Debian and in fact still draws the majority of its packages from Debian repositories. Like the relationships between son and father relations between Ubuntu and Debian are not always smooth :).

---

### Post by honey_bee on 2012-12-03
thanks for your kind reply. Well so we can say that Debian is the Father and Ubuntu is his son :)

---

### Post by redmk2 on 2012-12-03
> **honey_bee said:**
> thanks for your kind reply. Well so we can say that Debian is the Father and Ubuntu is his son :)

More like Debian is the upstream basis of the Ubuntu distro. Most of the packages are maintained by Debian maintainers.  Some packages are Ubuntu specific.

The big difference in Linux distros in general is the packages.  There is Redhat/CentOS/SUSE using RPM (yum) and Debian/Ubuntu using deb(dpkg/APT).  There are others (i.e Gentoo) but the main distros are either RPM or deb based.  The packages rely on certain file structures and commands that are unique to the distro type (RPM or deb).

---

### Post by honey_bee on 2012-12-04
well can you guide me that what are other linux distributions which are drive from Debian. Ubuntu is one of them. :) 

OpenDSB,FreeDSB,Linux Mint,Slax,Puppy Linux etc etc Are these are also from Debian family?


thanks,
honey

---

### Post by malspa on 2012-12-04
Check out the Linux timeline to see the different distro families: [http://futurist.se/gldt/](http://futurist.se/gldt/)

---

### Post by redmk2 on 2012-12-04
> **honey_bee said:**
> well can you guide me that what are other linux distributions which are drive from Debian. Ubuntu is one of them. :) 

OpenDSB,FreeDSB,Linux Mint,Slax,Puppy Linux etc etc Are these are also from Debian family?


thanks,
honey

There are tons of images that have Linux or Debian or UNIX/Linux family trees.  Just Google Linux, Debian or UNIX/Linux family tree and look at the image section.  Anything with BSD in the name is not Linux at all.  It is BSD UNIX.

---

### Post by mcduck on 2012-12-04
> **honey_bee said:**
> well can you guide me that what are other linux distributions which are drive from Debian. Ubuntu is one of them. :) 

OpenDSB,FreeDSB,Linux Mint,Slax,Puppy Linux etc etc Are these are also from Debian family?


thanks,
honey

OpenBSD and FreeBSD are not Linux distributions, they are different versions of the BSD operating system.

Linux Mint is a derivative of Ubuntu, so in a way it is indeed also related to Debian.

Slax is based on Slackware. I'm not sure about current versiosn of Puppy, it's been ages since I've used that one... :D

---

### Post by honey_bee on 2012-12-04
The thing which i saw in  [http://futurist.se/gldt/](http://futurist.se/gldt/) is there are main three linux Flavor

1--Debiam
2--Slackware
3--RedHat


Rest of the linux is drived from these above linux distribution.

thanks
honey

---

### Post by malspa on 2012-12-04
> **honey_bee said:**
> The thing which i saw in  [http://futurist.se/gldt/](http://futurist.se/gldt/) is there are main three linux Flavor

1--Debiam
2--Slackware
3--RedHat


Rest of the linux is drived from these above linux distribution.

If you look more closely, you'll notice that there are other distros that are not derived from either of those three. Gentoo (on the Enoch branch) and Arch are just two examples, but there are many others.

---

### Post by Abhinav Kumar on 2012-12-04
Hi

Another detailed list is available on wikipedia
[http://upload.wikimedia.org/wikipedia/commons/8/8c/Gldt.svg](http://upload.wikimedia.org/wikipedia/commons/8/8c/Gldt.svg)

Regards,
Abhinav

---

### Post by Lyfang on 2012-12-04
> **redmk2 said:**
> There are tons of images that have Linux or Debian or UNIX/Linux family trees.  Just Google Linux, Debian or UNIX/Linux family tree and look at the image section.  Anything with BSD in the name is not Linux at all.  It is BSD UNIX.
There is also Debian GNU/kFreeBSD, where there is no proprietary AT&T Unix code that requires the AT&T software license. A downstream of Debian GNU/Linux is Ubuntu. Ubuntu (GNU/Linux) derives from Debian GNU/Linux. A downstream of Ubuntu is Linux Mint (GNU/Linux). Upstream components to Ubuntu are the Linux kernel and X.org package. I insert this image for better understanding of the *UNIX/Linux family trees*:
[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/7/77/Unix_history-simple.svg/800px-Unix_history-simple.svg.png[/IMG]

---

### Post by honey_bee on 2012-12-04
oh yes i look closly. thanks for the correction.One thing more I want to discuss that at server side mostly people use Red Hat Enterprise and medium or small organizations use CentOS or Fedora 

Why people not prefer Debian ? Even it has a lot of software varity than Red Hat or Fedora.

thanks once again for guiding me,
honey.

---

### Post by mcduck on 2012-12-04
> **honey_bee said:**
> oh yes i look closly. thanks for the correction.One thing more I want to discuss that at server side mostly people use Red Hat Enterprise and medium or small organizations use CentOS or Fedora 

Why people not prefer Debian ? Even it has a lot of software varity than Red Hat or Fedora.

thanks once again for guiding me,
honey.

Red Hat has a large company backing it, and  provides enterprise version and commercial support for their distribution.

If you are the guy deciding which operating system your company should use, you'll want something that allows you to forward the blame to somebody else in case things go wrong. And having the commercial support gives that option. ;)

Debian on the other hand is pretty much a community-driven project, and while there are companies providing support for it, it's not first-hand like with Red Hat.

---

