---
title: "MAJOR apt-get bug :O :O"
date: 2007-07-14
forum: General Help
---

### Post by Sockerdrickan on 2007-07-14
I try to do anything that has to do with apt-get and I get "The package needs to be reinstalled, but I couldn't find any packages to do that..." :S

---

### Post by Pom2122 on 2007-07-14
What do you get with the command

```
sudo dpkg -C
```

---

### Post by Sockerdrickan on 2007-07-14
Följande paket är i oordning på grund av grava problem när de
installerades. De måste ominstalleras om de (och paket som beror på
dem) ska fungera korrekt:
 pidgin               


Something like:

These packages are in dissorder because off the problems caused when they were installed. They have to be reinstalled if they (and the packages that depends on them) want to work correct:
pidgin

---

### Post by Pom2122 on 2007-07-14
Okay, did this happen when you were trying to install pidgin? Is pidgin working?

Let's see if we can get any more information from dpkg.

```
sudo dpkg -s pidgin
```

That will give you the installation status of the package: pidgin.

---

### Post by Sockerdrickan on 2007-07-14
Package: pidgin
Status: install reinstreq half-installed
Priority: optional
Section: net
Version: 1:2.0.2-1~getdeb1

---

### Post by Sockerdrickan on 2007-07-14
I closed the deb installer when I was installing it, but that was about 1 second before it actually was done, the problems came after...

---

### Post by Pom2122 on 2007-07-14
> I closed the deb installer when I was installing it, but that was about 1 second before it actually was done, the problems came after...

That was probably it. It is quite possible that pidgin would require some setup and you closed before it could go through.

First try:

```
sudo dpkg-reconfigure pidgin
```

That will restart the configuration process if pidgin has a debconf setup.
If nothing happens then try:

```
sudo apt-get install --reinstall pidgin
```

This will reinstall pidgin.
:)

---

### Post by Sockerdrickan on 2007-07-14
1. gives me pidgin is broken or not completely installed
2. gives me pidgin have to be reinstalled but no archives found for it

Can't I just remove stuff?

---

### Post by jocko on 2007-07-14
Did you by any chance try to install pidgin from a downloaded .deb file using gdebi?
In that case the apt system probably don't know where to find the .deb-file, so it can't fix the error automagically...
If this is the case it should work if you re-install pidgin from the same .deb file (just double click it to let gdebi do it).

---

### Post by Pom2122 on 2007-07-14
Those are some odd errors. :confused:

First some safety:

```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.safe

```
Let's start with the least destructive. :)

```
sudo apt-get remove --purge pidgin
```

The next removes and purges:

```
sudo dpkg -r -P pidgin
```

A little heavier duty:

```
sudo dpkg -r --force-remove-reinstreq pidgin
```

---

### Post by Sockerdrickan on 2007-07-15
Aww, I reformated already lol =( But thanks, I'll keep this thread in mind if I need it again! :D

---

