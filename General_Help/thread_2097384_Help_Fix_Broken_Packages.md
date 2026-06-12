---
title: "Help Fix Broken Packages"
date: 2012-12-23
forum: General Help
---

### Post by DBQ on 2012-12-23
Hi everybody.

I ended up with some broken packages after installing updates.

When I do sudo apt-get -f install, I get the same error which is

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  libembryo0
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  libefl
The following NEW packages will be installed:
  libefl
0 upgraded, 1 newly installed, 0 to remove and 8 not upgraded.
6 not fully installed or removed.
Need to get 0 B/1,389 kB of archives.
After this operation, 3,617 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 478527 files and directories currently installed.)
Unpacking libefl (from .../libefl_201212221917-539~quantal1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libefl_201212221917-539~quantal1_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libevas.so.1.7.99', which is also in package libevas1 201210080233-5400~quantal1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libefl_201212221917-539~quantal1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I also tried using sudo apt-get autoremove to no avail.

I need this fixed so I can install iotop in order to continue debugging the issue in this thread: [http://ubuntuforums.org/showthread.php?t=2074692](http://ubuntuforums.org/showthread.php?t=2074692)

---

### Post by Cookieh on 2012-12-23
Enter the Recovery Mode by holding shift after the start up logo. If you see Ubuntu logo you done it too late. From the recovery mode, navigate to initiate network mode or something like that which says network. Then go up to fix broken packages or update the packages. This will force update the packages and it should repair the broken ones.

---

### Post by Pjotr123 on 2012-12-23
You can also use Synaptic Package Manager to repair broken packages from within your normal desktop. :)

1. Install Synaptic
2. Launch Synaptic
3. Synaptic panel: Edit - Fix Broken Packages

---

### Post by rnerwein on 2012-12-23
> **DBQ said:**
> Hi everybody.

I ended up with some broken packages after installing updates.

When I do sudo apt-get -f install, I get the same error which is

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  libembryo0
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  libefl
The following NEW packages will be installed:
  libefl
0 upgraded, 1 newly installed, 0 to remove and 8 not upgraded.
6 not fully installed or removed.
Need to get 0 B/1,389 kB of archives.
After this operation, 3,617 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 478527 files and directories currently installed.)
Unpacking libefl (from .../libefl_201212221917-539~quantal1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libefl_201212221917-539~quantal1_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libevas.so.1.7.99', which is also in package libevas1 201210080233-5400~quantal1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libefl_201212221917-539~quantal1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```I also tried using sudo apt-get autoremove to no avail.

I need this fixed so I can install iotop in order to continue debugging the issue in this thread: [http://ubuntuforums.org/showthread.php?t=2074692](http://ubuntuforums.org/showthread.php?t=2074692)
hy
give: dpkg --configure -a --peding  a try.
cheers

---

### Post by DBQ on 2012-12-23
I tried all of the above approaches, except the recovery console.

All of them fail with pretty much the same error.

I will try the recovery console, but I have doubts it will help (I want to be wrong).

Any other ideas?

---

### Post by ibjsb4 on 2012-12-23
```
sudo apt-get clean
```

---

### Post by mc4man on 2012-12-23
You could use dpkg to force an overwrite but why do you have that ppa installed that's providing libefl_201212221917-539 & what does this have to do with installing iotop?
(& why do you have libevas1 installed?

---

### Post by DBQ on 2012-12-23
> **mc4man said:**
> You could use dpkg to force an overwrite but why do you have that ppa installed that's providing libefl_201212221917-539 & what does this have to do with installing iotop?
(& why do you have libevas1 installed?


I am not sure why it's there. At one point I was trying out many desktop environments (e.g. xmonad, mate, enlightenment, KDE, etc). Perhaps this is an artifact of those experiments.

P.S. I also tried apt-get clean, but it did not solve the problem.

---

### Post by Frogs Hair on 2012-12-23
```
libevas
```

This is an E17 package and if you were using this ppa:hannes-janetzek/enlightenment-svn there were two broken package problems reported with it yesterday 12-22. This was a PPA maintainer error and he was notified.

---

### Post by DBQ on 2012-12-23
I would not mind uninstalling enlightenment -- I do not use it.

Whats the best way?

---

### Post by Frogs Hair on 2012-12-23
That depends how E17 was installed . Did you use a PPA or the packages in the Ubuntu repository ?

---

### Post by mc4man on 2012-12-23
> **DBQ said:**
> I am not sure why it's there. At one point I was trying out many desktop environments (e.g. xmonad, mate, enlightenment, KDE, etc). Perhaps this is an artifact of those experiments.

P.S. I also tried apt-get clean, but it did not solve the problem.

Well then likely no reason to have it or  libevas1 installed. You could simulate removing & see
```
sudo apt-get -s purge libevas1 libefl
```
If it looks good remove the " -s " & rerun.
Then  disable the ppa & update your sources.

---

