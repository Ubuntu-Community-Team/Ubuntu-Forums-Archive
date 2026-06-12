---
title: "Wine? Yes please..."
date: 2007-08-11
forum: General Help
---

### Post by ZekeXaero on 2007-08-11
Okay I'm sure you've all heard this before: Oh no how do I get wine running?! Well Here it is agian :( I've looked everywhere I could think of and Nothing I've done has worked. THe latest try has given me this:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libasound2 (> 1.0.12) but 1.0.10-2ubuntu4 is to be installed
        Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is to be installed
        Depends: libgcc1 (>= 1:4.1.2) but 1:4.0.3-1ubuntu5 is to be installed
        Depends: libgphoto2-2 (>= 2.3.0) but 2.1.6-5.2ubuntu8 is to be installed
        Depends: libgphoto2-port0 (>= 2.3.0) but 2.1.6-5.2ubuntu8 is to be installed
        Depends: libstdc++6 (>= 4.1.2) but 4.0.3-1ubuntu5 is to be installed
        Depends: libxml2 (>= 2.6.27) but 2.6.24.dfsg-1ubuntu1 is to be installed
        Depends: libxslt1.1 (>= 1.1.20) but 1.1.15-1ubuntu1 is to be installed
E: Broken packages

I'm running a freshly installed (from the disk) Ubuntu 6.06.1

---

### Post by davidsrsb on 2007-08-11
Its worth starting with a clean Feisy 7.04 install. Wine is a very fast evolving piece of software. The version of Wine defaulted to in 7.04 is fairly painless to install.

---

### Post by vexorian on 2007-08-11
are you using sudo apt-get install to install wine?

Cause it looks like you are using a .deb instead...

if you want you may try to update/install those packages manually, although it seems better to me if you tried to install WINE from synaptic

---

### Post by ZekeXaero on 2007-08-11
I've tried everything I can find but  That latest I believe was sudo apt get...I suppose From now on I'm going to log everything I do in the terminal because I'm completely lost. I ran Kubuntu a wile back and after adding a line to some text file Everything about wine worked :confused: Unfortunately that system got fried by lightning :( If perhaps some codes were posted I could either try them or if I recognise them as ones I've used, say so? (It probably doesn't help my situation that I know verry little about Linux terminals as I'm just now swiching over from windows xp due to a virus) Any codes posted should probably have some kind of instructions on how to use them otherwise It'll probably just blow up on me... kinda like the last win 98 computer I owned lol:biggrin:


Sudo apt-get install:

-desktop:~$ sudo apt-get install wine
Password:
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
  wine: Depends: libasound2 (> 1.0.12) but 1.0.10-2ubuntu4 is to be installed
        Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is to be installed
        Depends: libgcc1 (>= 1:4.1.2) but 1:4.0.3-1ubuntu5 is to be installed
        Depends: libgphoto2-2 (>= 2.3.0) but 2.1.6-5.2ubuntu8 is to be installed        Depends: libgphoto2-port0 (>= 2.3.0) but 2.1.6-5.2ubuntu8 is to be installed
        Depends: libstdc++6 (>= 4.1.2) but 4.0.3-1ubuntu5 is to be installed
        Depends: libxml2 (>= 2.6.27) but 2.6.24.dfsg-1ubuntu1 is to be installed        Depends: libxslt1.1 (>= 1.1.20) but 1.1.15-1ubuntu1 is to be installed
E: Broken packages

---

### Post by Bofur on 2007-08-11
Have you tried installing via Synaptic. If you did then I don't know what to tell you.. it seems as though some of the dependencies Wine requires may be corrupt. All I can recommend at this time is a clean install of Ubuntu, unless someone else knows how to fix this problem.

Another thing to check if to go into synaptic and check if all these packages are correctly installed and working properly:
  wine: Depends: libasound2 (> 1.0.12) but 1.0.10-2ubuntu4 is to be installed
        Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is to be installed
        Depends: libgcc1 (>= 1:4.1.2) but 1:4.0.3-1ubuntu5 is to be installed
Depends: libgphoto2-2 (>= 2.3.0) but 2.1.6-5.2ubuntu8 is to be installed Depends: libgphoto2-port0 (>= 2.3.0) but 2.1.6-5.2ubuntu8 is to be installed
        Depends: libstdc++6 (>= 4.1.2) but 4.0.3-1ubuntu5 is to be installed
Depends: libxml2 (>= 2.6.27) but 2.6.24.dfsg-1ubuntu1 is to be installed Depends: libxslt1.1 (>= 1.1.20) but 1.1.15-1ubuntu1 is to be installed

---

### Post by ruibernardo on 2007-08-11
Hi ZeKeXaero,

please try the following:

```
 sudo apt-get install -f
```

It should try to install wine again and fix the broken dependencies by installing them.

Cheers.

---

### Post by ZekeXaero on 2007-08-11
I tried the -f and it did nothing. however if someone could explain this Synaptic perhaps I could attempt that?

---

### Post by trak87 on 2007-08-11
> ...if someone could explain this Synaptic...

System -> Administration -> Synaptic Package Manager

---

### Post by ZekeXaero on 2007-08-11
I tried installing the missing packages through  the Synaptic Package Manager but still came up with some strange errors. I've recently discovered that Xubuntu is probably more suited to my system specs and by getting Feisty I probably won't come up with so many errors. However any tips on getting wine in Xu would be nice. Oh also before I swich, Tips on burning an iso to cd or possibly  running the iso without burning it to cd would also be helpful- [edit] Uhh... noting that  the total is 931.3 MB preferably running *without* burning it to cd seeing as that wouldn't fit on a cd that holds 700 MB [re-edit] forget disk sizes My burner won't do it's job... [update] The burner's working now however every time I burn a cd it refuses to load the installer saying it's corrupt. upon further inspection it gives me a specific corrupt file--> ./pool/main/b/binutils/binutils-static-udeb_2.17.20070103cvs-0ubuntu2_i386.udeb <-- saying that it fails the MD5 checksum verification. Now this was burned directly from the united states Xubuntu alternate install iso downloaded from [http://www.xubuntu.org/get](http://www.xubuntu.org/get). Is this Iso corrupt? or is my burning software corrupting it for me?

---

