---
title: "TZDATA help"
date: 2006-10-08
forum: General Help
---

### Post by LORD_PoLvO on 2006-10-08
hey people i am havng trouble getting the package tzdata installed.

first i tried getting the DEB package from here

[http://packages.debian.org/unstable/libs/tzdata]("http://packages.debian.org/unstable/libs/tzdata")

i went to install the package using Gdebi but got the following error

```
dpkg-deb: subprocess paste killed by signal (broken pipe)
```

i then tried to install using dpkg-i also getting the following error

```
daniel@daniel-desktop:~$ sudo dpkg -i /home/daniel/Desktop/tzdata_2006l-1_all.deb
(Reading database ... 97817 files and directories currently installed.)
Unpacking tzdata (from .../Desktop/tzdata_2006l-1_all.deb) ...
dpkg: error processing /home/daniel/Desktop/tzdata_2006l-1_all.deb (--install):
 trying to overwrite `/usr/share/zoneinfo/Africa/Algiers', which is also in package locales
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/daniel/Desktop/tzdata_2006l-1_all.deb
daniel@daniel-desktop:~$

```

then i tried to downlaod the rpm from here

[http://rpm.pbone.net/index.php3/stat/4/idpl/1981524/com/tzdata-2005i-2.noarch.rpm.html]("http://rpm.pbone.net/index.php3/stat/4/idpl/1981524/com/tzdata-2005i-2.noarch.rpm.html")

i converted using alien to deb and then tried to install again getting this error 

```
daniel@daniel-desktop:~$ sudo dpkg -i /home/daniel/Desktop/tzdata_2005i-3_all.deb
Password:
(Reading database ... 97817 files and directories currently installed.)
Unpacking tzdata (from .../Desktop/tzdata_2005i-3_all.deb) ...
dpkg: error processing /home/daniel/Desktop/tzdata_2005i-3_all.deb (--install):
 trying to overwrite `/usr/share/zoneinfo/Africa/Abidjan', which is also in package locales
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/daniel/Desktop/tzdata_2005i-3_all.deb
daniel@daniel-desktop:~$

```

all these erros are the same and i havent been able to track down the source of the error can anyone please help me sort this out as i need this package as a dependency for most of the other packages i need to install plesae if some one can help i would greatly appreciate it,

PoLvO

---

### Post by mrojas73 on 2007-10-20
Same thing happened to me, how do we resolve this?

Thank in advance for any help.

---

### Post by Stuart_1745 on 2007-10-20
Im having the same problem as well. cant add/update/remove any thing because 
E: tzdata: subprocess post-installation script returned error exit status 10

it also returns this when I try and reinstall tzdata

also I seam to remember tzdata being in my updates today, so maybe thats got something to do with it.

{edit}

ok found[ this]("https://bugs.launchpad.net/ubuntu/+source/tzdata/+bug/125349") bug report 

and all I had to do was change my time zone from North Decota to Chicago and then the problem was fixed

---

