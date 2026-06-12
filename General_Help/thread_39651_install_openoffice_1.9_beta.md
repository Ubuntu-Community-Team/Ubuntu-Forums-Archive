---
title: "install openoffice 1.9 beta?"
date: 2005-06-06
forum: General Help
---

### Post by not_yet on 2005-06-06
hello all,

trying to install openoffice 1.9

I have downloaded the files and all the rpm's are in one folder

I get the following error  (as root)

rpm -Uvih *rpm
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - No such file or directory (2)
error: cannot open Packages database in /var/lib/rpm

suggestions  :???: 

thanks

---

### Post by moopere on 2005-06-06
[QUOTE=not_yet]hello all,

trying to install openoffice 1.9

I have downloaded the files and all the rpm's are in one folder

I get the following error  (as root)

rpm -Uvih *rpm
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - No such file or directory (2)
error: cannot open Packages database in /var/lib/rpm

suggestions  :???: 

thanks[/QUOTE]

Yep, use alien as stated in the error message...I'm serious, don't install other systems packages on debian or you'll lose the benefits of apt and dpkg package management.

type alien, followed by a space and the name of the rpm, it will convert the rpm to a .deb which you can then install using dpkg -i packagename.deb

Having said that though, why start with an RPM at all?  Why not use the OOo2 debian files in universe?

Cheers,
Craig

---

### Post by not_yet on 2005-06-06
moopere wrote:

> Having said that though, why start with an RPM at all? Why not use the OOo2 debian files in universe?

thanks for the reply :smile: 

I'm just a bit confused / I'm using Ubuntu 5.04

I don't think I can get to the latest openoffice snapshot with apt?

thats why I downed the rpm's

can it be done with apt?

when I try apt, it says OO is not avaiable.

> notyet@ubuntu:~$ sudo apt-get install 00o2
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package 00o2


cheers

---

### Post by moopere on 2005-06-06
[QUOTE=not_yet]moopere wrote:



thanks for the reply :smile: 

I'm just a bit confused / I'm using Ubuntu 5.04

I don't think I can get to the latest openoffice snapshot with apt?

thats why I downed the rpm's

can it be done with apt?

when I try apt, it says OO is not avaiable.




cheers[/QUOTE]

Yep, well, fair enough, I doubt that 5.04 Hoary has the very latest snapshot of OOo2.  It has whatever snapshot was available at the time Hoary was frozen.

If you really really must have the very latest snapshot I'm guessing that you will need to look in the breezy repositories.  (need to change your /etc/apt/sources file for that).

Now, if you decide to do this, you're likely to come up against some pretty scary stuff.  Breezy is making the transition to a new compiler version thats not guarenteed ABI compatible with previous versions.  You could decide to upgrade your hoary system to breezy but its probably too immature for general use just yet.

By the way, using RPM's made for specific variations of RedHat (or similar) is also potentially scary - you just won't know what libraries etc the target system has as default install and therefore can find yourself right in the middle of "RPM Hell" as would be familiar to most Linux users who run Distro's using RPM as their package management.

If you really really really must have the latest snapshot and don't want to go for Breezy or RPM hell, you might want to consider compiling the latest snapshot yourself.  Or have a chat to the maintainers of "ubuntu backports", they might well have a backport of a recent snapshot already good to go for Hoary.

Cheers,
Craig

---

### Post by jasplund on 2005-06-06
You can find deb's of version 1.9.105 at [http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m105/Build-1/](http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m105/Build-1/)


Johan

---

