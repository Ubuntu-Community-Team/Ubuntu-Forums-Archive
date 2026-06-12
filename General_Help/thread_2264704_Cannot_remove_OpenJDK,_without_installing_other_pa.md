---
title: "Cannot remove OpenJDK, without installing other packages"
date: 2015-02-09
forum: General Help
---

### Post by Vesnog on 2015-02-09
Greetings,

I am running Ubuntu 14.04.1 64-bit and I would like to remove the packages **openjdk-7-* **since I already have Oracle Java installed. But when I try to remove them via the command line I get the following weird response which suggests to install the earlier releases of the very packages I would like to purge. How can I remedy this situation and remove OpenJDK for good? Any help and/or suggestions are welcome and appreciated.

```
 $ sudo apt-get purge openjdk-7-*Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'openjdk-7' for regex 'openjdk-7-*'
Note, selecting 'openjdk-7-jre-zero' for regex 'openjdk-7-*'
Note, selecting 'openjdk-7-jdk' for regex 'openjdk-7-*'
Note, selecting 'openjdk-7-jre-headless' for regex 'openjdk-7-*'
Note, selecting 'openjdk-7-dbg' for regex 'openjdk-7-*'
Note, selecting 'openjdk-7-jre-lib' for regex 'openjdk-7-*'
Note, selecting 'uwsgi-plugin-jvm-openjdk-7' for regex 'openjdk-7-*'
Note, selecting 'openjdk-7-jre' for regex 'openjdk-7-*'
Note, selecting 'openjdk-7-source' for regex 'openjdk-7-*'
Note, selecting 'openjdk-7-demo' for regex 'openjdk-7-*'
Note, selecting 'openjdk-7-doc' for regex 'openjdk-7-*'
Note, selecting 'uwsgi-plugin-jwsgi-openjdk-7' for regex 'openjdk-7-*'
Package 'openjdk-7' is not installed, so not removed
Package 'uwsgi-plugin-jvm-openjdk-7' is not installed, so not removed
Package 'uwsgi-plugin-jwsgi-openjdk-7' is not installed, so not removed
Package 'openjdk-7-dbg' is not installed, so not removed
Package 'openjdk-7-demo' is not installed, so not removed
Package 'openjdk-7-doc' is not installed, so not removed
Package 'openjdk-7-jdk' is not installed, so not removed
Package 'openjdk-7-source' is not installed, so not removed
Package 'openjdk-7-jre-lib' is not installed, so not removed
Package 'openjdk-7-jre-zero' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  launchpad-getkeys linux-image-3.13.0-43-generic
  linux-image-extra-3.13.0-43-generic python-keyring python-launchpadlib
  python-lazr.restfulclient python-lazr.uri python-oauth python-secretstorage
  python-wadllib xclip yad
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  icedtea-6-jre-cacao icedtea-6-jre-jamvm icedtea-netx openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib ttf-dejavu-extra
Suggested packages:
  icedtea-plugin sun-java6-fonts fonts-ipafont-gothic fonts-ipafont-mincho
  ttf-telugu-fonts ttf-oriya-fonts ttf-kannada-fonts ttf-bengali-fonts
The following packages will be REMOVED:
  default-jre* default-jre-headless* octave* openjdk-7-jre*
  openjdk-7-jre-headless*
The following NEW packages will be installed:
  icedtea-6-jre-cacao icedtea-6-jre-jamvm icedtea-netx openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib ttf-dejavu-extra
0 upgraded, 7 newly installed, 5 to remove and 3 not upgraded.
Need to get 37.8 MB of archives.
After this operation, 3,014 kB disk space will be freed.
Do you want to continue? [Y/n] 

```
Furthermore, what does the first part of the output mean?

---

### Post by mc4man on 2015-02-09
You probably have some package(s) that depend on what you're trying to remove & that package(s) allow what's to be installed to satisfy the depends instead.

However you installed the Oracle version hasn't replaced what the open packages provide in terms of package management.
If the Oracle version is being used then I'd just leave well enough alone. If really set on removing then you'd need to 'inform' the pm system that the depend(s) are satified. One way would be thru a or some equivs packages though that could be a bit complicated in this case.
Other ways would include editing the control files of the installed packages that are causing this, again, why bother?

---

### Post by Vesnog on 2015-02-09
Actually I would like to make it right since it bugs me a lot due to my meticulousness.  Is there a command with which I can learn exactly which packages depend on these two packages, namely openjdk-7-jre and openjdk-7-jre-headless? I think there should be, apart from that I have used **equivs package **while installing TexLive 2014 so I think I can take care of it.

---

### Post by Vesnog on 2015-02-09
> **mc4man said:**
> You probably have some package(s) that depend on what you're trying to remove & that package(s) allow what's to be installed to satisfy the depends instead.

However you installed the Oracle version hasn't replaced what the open packages provide in terms of package management.
If the Oracle version is being used then I'd just leave well enough alone. If really set on removing then you'd need to 'inform' the pm system that the depend(s) are satified. One way would be thru a or some equivs packages though that could be a bit complicated in this case.
Other ways would include editing the control files of the installed packages that are causing this, again, why bother?

Actually I found the culprit it was the program **Geogebra** that I installed from the Ubuntu Software Center, I determined that it was how **openjdk-7-jre and openjdk-7-jre-headless **were installed by running the following commands:

```
ongun@VesnogXPS:~$ aptitude why openjdk-7-jre
i   geogebra    Depends default-jre | java5-runtime | java6-runtime | java7-runtim
                        e                                                         
i A default-jre Depends openjdk-7-jre (>= 7~u3-2.1.1)                             
ongun@VesnogXPS:~$ aptitude why openjdk-7-jre-headless 
i   octave               Depends default-jre-headless                  
i A default-jre-headless Depends openjdk-7-jre-headless (>= 7~u3-2.1.1)



```

---

### Post by mc4man on 2015-02-09
ck. out man apt-cache 
(if using unity a bit more readable if opened via the  Dash, Open Dash home > type >  manpages:apt-cache

probably apt-cache  rdepends packagename though you can add some options like - 
apt-cache rdepends --installed --no-suggests openjdk-7-jre 
ect. ect.

Or use synaptic & see what happens when you mark some of them for removal, note that currently when causing a break in synaptic you need to reload the sources to get useful again (sometimes twice

---

### Post by Vesnog on 2015-02-09
> **mc4man said:**
> ck. out man apt-cache 
(if using unity a bit more readable if opened via the  Dash, Open Dash home > type >  manpages:apt-cache

probably apt-cache  rdepends packagename though you can add some options like - 
apt-cache rdepends --installed --no-suggests openjdk-7-jre 
ect. ect.

Or use synaptic & see what happens when you mark some of them for removal, note that currently when causing a break in synaptic you need to reload the sources to get useful again (sometimes twice

Doing that before trying to remove, thanks for the update. I was just editing my post at the moment. Now when I try to uninstall it **openjdk-7-jre-headless **the package manager also tries to uninstall **octave **which is weird in my opinion.

EDIT: Sorry, after updating the problems were resolved I appreciate your help.

---

