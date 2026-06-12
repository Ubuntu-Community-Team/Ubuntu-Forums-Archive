---
title: "Cant install some packages (you have held broken packages)"
date: 2016-07-04
forum: General Help
---

### Post by mrcameronnewton on 2016-07-04
Hi there.
So I'm in a bit of a problem here.
I'm trying to install some packages, and I get the error: E: Unable to correct problems, you have held broken packages.I have looked at countless forums and tried the following


[LIST=1]
[*]Installing aptitude
[*]using apt-get install -f
[*]Erased the package list, and added the default
[*]Added i386 (I'm running amd64)
[*]ran apt-get update and upgrade countless times
[*]I have also ran a command to check 'Held packages'. There are none according to the system
[/LIST]
Skype and Wine are subduing to this issue. I have tried downloading the .deb files and running dpkg but it still shows the same error
Any ideas?

---

### Post by Impavidus on 2016-07-05
Which version of Ubuntu?

Can you show us the complete output of the commands```
sudo apt-get update
sudo apt-get upgrade
```That should tell us what's going on.

---

