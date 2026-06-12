---
title: "Apt-daemon kept back"
date: 2015-10-21
forum: General Help
---

### Post by awamunro on 2015-10-21
The Update Manager on wilk will not run and says "You stopped the check for updates"
Further investigation showed that dependencies are not being met and the terminal on updating/upgrading shows:

> The following packages have been kept back:  aptdaemon python-aptdaemon.gtk3widgets
  python3-aptdaemon.gtk3widgets python3-aptdaemon.pkcompat

This has been there for at least a month if not more and release of wily is iminent

---

### Post by ian-weisser on 2015-10-21
By 'wilk', one assumes you mean 'Wily'?
There are NO other error messages or warnings in the terminal?

Try installing one of those held packages (use --simulate) and see if apt provides a lot more detail on the problem. Sounds like a version conflict.

---

### Post by mc4man on 2015-10-21
aptdaemon updated about a week ago with no issues doing so, current is 1.1.1+bzr982-0ubuntu14
What does apt-cache policy aptdaemon* show?

---

### Post by ronacc on 2015-10-21
apt daemon and  other apt packages have been held on my 64bit Gnome flavor system for a several days due to unmet dependencies . Using "fix broken" in synaptics does nothing , returns no info about what dependencies are unmet.

---

### Post by mc4man on 2015-10-21
> **ronacc said:**
> apt daemon and  other apt packages have been held on my 64bit Gnome flavor system for a several days due to unmet dependencies . Using "fix broken" in synaptics does nothing , returns no info about what dependencies are unmet.
sudo aptitude -s upgrade may be more informative (with or without the -s, may not matter in this case..

---

### Post by QDR06VV9 on 2015-10-21
> **ronacc said:**
> apt daemon and  other apt packages have been held on my 64bit Gnome flavor system for a several days due to unmet dependencies . Using "fix broken" in synaptics does nothing , returns no info about what dependencies are unmet.
Same here!

---

### Post by ronacc on 2015-10-21
> **mc4man said:**
> sudo aptitude -s upgrade may be more informative (with or without the -s, may not matter in this case..

it wants to remove 34 packages but not install apt etc .

---

### Post by QDR06VV9 on 2015-10-21
Here is what i am showing now for upgrade && dist-upgrade
```
sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  syslinux-common
The following packages have been kept back:
  aptdaemon conky-all libavfilter-ffmpeg5 python-aptdaemon.gtk3widgets
  python3-aptdaemon.gtk3widgets
The following packages will be upgraded:
  usb-creator-common usb-creator-gtk
2 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
```
Conky I have Pinned(Hold)
```
apt-cache policy aptdaemon
aptdaemon:
  Installed: 1.1.1+bzr982-0ubuntu8
  Candidate: 1.1.1+bzr982-0ubuntu14
  Version table:
     1.1.1+bzr982-0ubuntu14 0
        500 http://archive.ubuntu.com/ubuntu/ wily/main amd64 Packages
 *** 1.1.1+bzr982-0ubuntu8 0
        100 /var/lib/dpkg/status



```

---

### Post by sgage on 2015-10-21
No problems with aptdaemon here - using repo 'Server for United States'.

---

### Post by ronacc on 2015-10-21
looking at  "properties" for 1.1.1+bzr982-0ubuntu14  in synaptics it says it breaks software center  .

---

### Post by QDR06VV9 on 2015-10-21
Huumm?
Using main sever here.
But according to mc4man I am using the correct version.
So very confused as of now??

---

### Post by QDR06VV9 on 2015-10-21
> **ronacc said:**
> looking at  "properties" for 1.1.1+bzr982-0ubuntu14  in synaptics it says it breaks software center  .
I don't have software center installed but breaks things that I need.
So I will wait to see if it gets sorted.
Regards

---

### Post by sgage on 2015-10-21
> **ronacc said:**
> looking at  "properties" for 1.1.1+bzr982-0ubuntu14  in synaptics it says it breaks software center  .

It didn't break my software center :KS   My apt package system seems to be healthy and consistent - I wonder what's going on? Are some repos not synced up?

---

### Post by ronacc on 2015-10-21
shouldn't be a repo problem everything else is updating normally . It will all sort itself when I do a fresh install for XX ( maybe ) :p

---

### Post by mc4man on 2015-10-21
> **ronacc said:**
> looking at  "properties" for 1.1.1+bzr982-0ubuntu14  in synaptics it says it breaks software center  .

It's " Breaks: software-center (<1.1.21)", Sc is currently @13.10-0ubuntu12 so obviously well past 1.1.xx which was lucid times..

---

### Post by ronacc on 2015-10-21
the properties were for aptdaemon 1.1.1+bzr982-0ubuntu14 . which is the current version that won't upgrade , the installed version is 1.1.1+bzr982-0ubuntu9 . My SC,is or was until I removed it ( no help )  13.10-0ubuntu12 .

---

### Post by awamunro on 2015-10-22
> **ian-weisser said:**
> By 'wilk', one assumes you mean 'Wily'?
There are NO other error messages or warnings in the terminal?

Try installing one of those held packages (use --simulate) and see if apt provides a lot more detail on the problem. Sounds like a version conflict.
I tried installing aptdaemon using simulate and get 

Some packages could not be installed. This may mean that you haverequested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 aptdaemon : Depends: python3-aptdaemon (= 1.1.1+bzr982-0ubuntu14) but 1.1.1+bzr982-0ubuntu9 is to be installed
E: Unable to correct problems, you have held broken packages.
alistair@alistair-Study:~$

---

### Post by awamunro on 2015-10-23
> **awamunro said:**
> 


The following packages have unmet dependencies.
 aptdaemon : Depends: python3-aptdaemon (= 1.1.1+bzr982-0ubuntu14) but 1.1.1+bzr982-0ubuntu9 is to be installed
E: Unable to correct problems, you have held broken packages.
alistair@alistair-Study:~$

I did a Package Force  install of 1.1.1+bzr928-0ubuntu9 and all is now well!
Has not broken anything!

---

### Post by cariboo on 2015-10-23
Moved to General Help, as Wily has been released.

---

### Post by slickymaster on 2015-10-30
Just for information:

[https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/1504242](https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/1504242) and [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1439769](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1439769)

---

