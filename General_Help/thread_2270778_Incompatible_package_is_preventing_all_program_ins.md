---
title: "Incompatible package is preventing all program installs."
date: 2015-03-25
forum: General Help
---

### Post by zach29 on 2015-03-25
So I am getting the following issue whenever I try to install anything via the Ubuntu software center or via the terminal. 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gksu : Depends: libgksu2-0 (>= 2.0.8) but it is not going to be installed
 i965-va-driver : Breaks: i965-va-driver:i386 (!= 1.5.0-1) but 1.3.2-1 is to be installed
 i965-va-driver:i386 : Breaks: i965-va-driver (!= 1.3.2-1) but 1.5.0-1 is to be installed
 libva1 : Breaks: libva1:i386 (!= 1.5.0-1) but 1.3.1-3 is to be installed
 libva1:i386 : Breaks: libva1 (!= 1.3.1-3) but 1.5.0-1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

It comes from doing this. 
[COLOR=#DBDBDB][FONT=Arial]1). wget [/FONT][/COLOR][http://ftp.ubuntu.com/ubuntu/pool/universe/i/intel-vaapi-driver/i965-va-driver_1.3.2-1_i386.deb]("https://steamcommunity.com/linkfilter/?url=http://ftp.ubuntu.com/ubuntu/pool/universe/i/intel-vaapi-driver/i965-va-driver_1.3.2-1_i386.deb")
[COLOR=#DBDBDB][FONT=Arial]2). wget [/FONT][/COLOR][http://ftp.ubuntu.com/ubuntu/pool/universe/libv/libva/libva1_1.3.1-3_i386.deb]("https://steamcommunity.com/linkfilter/?url=http://ftp.ubuntu.com/ubuntu/pool/universe/libv/libva/libva1_1.3.1-3_i386.deb")
[COLOR=#DBDBDB][FONT=Arial]3). sudo dpkg -i libva1_1.3.1-3_i386.deb[/FONT][/COLOR]
[COLOR=#DBDBDB][FONT=Arial]4). sudo dpkg -i i965-va-driver_1.3.2-1_i386.deb

[/FONT][/COLOR]the issue is that this isn't compatible with the newest intel drivers that I got from Intel's auto update program. 

Any way I can fix this?

Thanks!![COLOR=#DBDBDB][FONT=Arial]


[/FONT][/COLOR]

---

### Post by dino99 on 2015-03-25
have you installed some non ubuntu's packages/apps  (like ppa and/or closed source) ?
if so, then purge them first, and then update again.

---

### Post by ian-weisser on 2015-03-25
> **zach29 said:**
> Any way I can fix this?
You have *several* problems. You must fix all of them before your package manager will work again.
The help below only tackles your tangled package management. It does not address your video problem.


> **zach29 said:**
> gksu : Depends: libgksu2-0 (>= 2.0.8) but it is not going to be installed
As 9d9 said, this looks like you tried to install a version of gksu that is inappropriate for the version of Ubuntu you are running. You have a *dependency conflict*. You have instructed your system to run two different versions of the same dependency on your system. It cannot. Those error messages are the system's way of begging you to resolve the conflict.

1) If you added it as a PPA or other non-Ubuntu source, disable or delete that source.
2) Delete the packages from your cache (sudo apt-get clean gksu libgksu2-0)
3) Refresh your package database (sudo apt-get update)
4) Install gksu from the Ubuntu repositories(sudo apt-get install gksu)



> **zach29 said:**
> i965-va-driver : Breaks: i965-va-driver:i386 (!= 1.5.0-1) but 1.3.2-1 is to be installed
 i965-va-driver:i386 : Breaks: i965-va-driver (!= 1.3.2-1) but 1.5.0-1 is to be installed
Wow, quite a situation you have created here. You're trying to install a i386 version of a package that *explicitly* breaks the common version, and reverse too.
Uninstall both packages. Delete those .deb files.
Reinstall the proper package for your version of Ubuntu from the proper Ubuntu Repositories.


> **zach29 said:**
> libva1 : Breaks: libva1:i386 (!= 1.5.0-1) but 1.3.1-3 is to be installed
 libva1:i386 : Breaks: libva1 (!= 1.3.1-3) but 1.5.0-1 is to be installed
Same problem.
Delete both. Reinstall from proper source for your version of Ubuntu.

---

### Post by zach29 on 2015-03-25
I got it working, thanks everyone.

---

