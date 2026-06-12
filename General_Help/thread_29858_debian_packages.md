---
title: "debian packages"
date: 2005-04-26
forum: General Help
---

### Post by minimal on 2005-04-26
Hi everyone,
I just installed Ubuntu 5.04 yesterday and was wondering if installing deb packages from the Debian Website is going to work.. In other words, are debian unstable packages compatible with ubuntu ?
thank you.

---

### Post by SGC on 2005-04-26
Sure, debian packages works just fine in ubuntu

---

### Post by heimo on 2005-04-26
The base for Ubuntu is Debian Sid (unstable), but I would recommend not to use Debian unstable packages (From Debian repositories) unless you have a very, very convincing reason to do so. To keep things simple, use Ubuntu repositories as the main source of packages. This is to avoid severe dependency problems.
 
Search
[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")
to find what you're looking for.
 
If you don't find what you're looking for (in main, restricted, universe or  multiverse), check some extra repositories:
[http://www.ubuntuguide.org/#extrarepositories]("http://www.ubuntuguide.org/#extrarepositories")

---

### Post by az on 2005-04-26
[QUOTE=minimal]Hi everyone,
I just installed Ubuntu 5.04 yesterday and was wondering if installing deb packages from the Debian Website is going to work.. In other words, are debian unstable packages compatible with ubuntu ?
thank you.[/QUOTE]


Yes and no.

Since debain packages try to solve dependancy problems and since you are in control of what is installed on your system, you may bork you dependancies and have to dump some packages if you mix repositories. 

Universe should have the packages that you need.  They were built for Ubuntu and will not bork you system.

---

