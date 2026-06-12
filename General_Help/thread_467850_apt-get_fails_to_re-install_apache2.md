---
title: "apt-get fails to re-install apache2"
date: 2007-06-08
forum: General Help
---

### Post by herbertng on 2007-06-08
sorry, i'm dumb, and here's what i did:

> apt-get remove apache2

then i found out there are still bunch of config files @ /etc/apache2 , so i rm -rf 'ed them 

later on, i wanted to reinstall apache2, so i did

> apt-get install apache2

and it says:

============================================
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  apache2
0 upgraded, 1 newly installed, 0 to remove and 33 not upgraded.
Need to get 0B/35.8kB of archives.
After unpacking 81.9kB of additional disk space will be used.
Selecting previously deselected package apache2.
(Reading database ... 21225 files and directories currently installed.)
Unpacking apache2 (from .../apache2_2.0.55-4ubuntu2.1_i386.deb) ...
Setting up apache2 (2.0.55-4ubuntu2.1) ...
=============================================

obviously, apache2 didnt' really get re-installed for 81.9kB :(

i think it has to do with the fact that i manually deleted some files. how do i force apt-get to get a clean re-installtion of apache2, or any other packages?

thanks in advance!

---

### Post by Crafty Kisses on 2007-06-08
> **herbertng said:**
> sorry, i'm dumb, and here's what i did:

> apt-get remove apache2

then i found out there are still bunch of config files @ /etc/apache2 , so i rm -rf 'ed them 

later on, i wanted to reinstall apache2, so i did

> apt-get install apache2

and it says:

============================================
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  apache2
0 upgraded, 1 newly installed, 0 to remove and 33 not upgraded.
Need to get 0B/35.8kB of archives.
After unpacking 81.9kB of additional disk space will be used.
Selecting previously deselected package apache2.
(Reading database ... 21225 files and directories currently installed.)
Unpacking apache2 (from .../apache2_2.0.55-4ubuntu2.1_i386.deb) ...
Setting up apache2 (2.0.55-4ubuntu2.1) ...
=============================================

obviously, apache2 didnt' really get re-installed for 81.9kB :(

i think it has to do with the fact that i manually deleted some files. how do i force apt-get to get a clean re-installtion of apache2, or any other packages?

thanks in advance!

You can try installing it from Synaptic. I'm not sure what exactly happened, but try that.

---

### Post by EndPerform on 2007-06-08
What happened is that apt-get reinstalled using the package it had already downloaded from the net.  If you want to clean those up:

```
sudo apt-get clean
```

will clear the downloaded packages out.

---

### Post by ddevore on 2007-06-12
I just started another post about this same topic. For some reason I didn't see this thread before I posted. Anyway I have done a clean and have not been able to get it to reinstall. 

I am stuck on this.. I am wondering if the package thinks something is there that is not.. is there some config files I can look at and possibly clean up manually to get it to forget the server. 

Also, I am trying this on a headless server so I can not use the Synaptic.

---

### Post by andymushu on 2007-06-12
go into synaptic, find the package, then right click and select "complete removal". then apply, then try to do sudo apt-get install

---

### Post by hebetude on 2007-11-11
Very odd that only synaptic can remove this correctly.  I did a complete removal on apache2 apache2.2-conf, reinstalled and it worked.  I believe the "common" package has all the config files in it, but removing/purging it with aptitude did not force it to install fresh config files.

Thanks andymushu

---

