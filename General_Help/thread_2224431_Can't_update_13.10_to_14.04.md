---
title: "Can't update 13.10 to 14.04"
date: 2014-05-16
forum: General Help
---

### Post by colinzealknows on 2014-05-16
For a few days the Updater would show the message "no updates, but there's a new Ubuntu version", but that message is gone now.

I tried running the command-line version, using the -d even, but all I get is "no newer version found".

Tried following this: [http://askubuntu.com/questions/451616/cant-update-to-14-04-because-software-updater-cant-set-new-software-channels](http://askubuntu.com/questions/451616/cant-update-to-14-04-because-software-updater-cant-set-new-software-channels) but nothing changed as well.

I made a 14.04 Live USB but there's no option to upgrade.

What else can I do?

Thank you.

---

### Post by philinux on 2014-05-16
Do a terminal update to 13.10 first.

sudo apt-get update && sudo apt-get dist-upgrade

post back any errors.

Also post your sources. 

cat /etc/apt/sources.list

---

### Post by colinzealknows on 2014-05-16
Thanks for the reply.
> **philinux said:**
> Do a terminal update to 13.10 first.

sudo apt-get update && sudo apt-get dist-upgrade

post back any errors.

Also post your sources. 

cat /etc/apt/sources.list

I issued the first command and it looks like a regular installation of software, is that the actual upgrade? I didn't go through because I want to be at home for this, I just ran it via remote ssh to check the result.

My sources are this (I got it from repogen.simplylinux.ch):

```
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://ca.archive.ubuntu.com/ubuntu/ saucy main restricted universe multiverse 
deb-src http://ca.archive.ubuntu.com/ubuntu/ saucy main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://ca.archive.ubuntu.com/ubuntu/ saucy-security main restricted universe multiverse 
deb http://ca.archive.ubuntu.com/ubuntu/ saucy-updates main restricted universe multiverse 
deb http://ca.archive.ubuntu.com/ubuntu/ saucy-proposed main restricted universe multiverse 
deb http://ca.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse 
deb-src http://ca.archive.ubuntu.com/ubuntu/ saucy-security main restricted universe multiverse 
deb-src http://ca.archive.ubuntu.com/ubuntu/ saucy-updates main restricted universe multiverse 
deb-src http://ca.archive.ubuntu.com/ubuntu/ saucy-proposed main restricted universe multiverse 
deb-src http://ca.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse 

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu saucy partner
deb-src http://archive.canonical.com/ubuntu saucy partner

###### Ubuntu Extras Repo
deb http://extras.ubuntu.com/ubuntu saucy main
deb-src http://extras.ubuntu.com/ubuntu saucy main


```

---

### Post by philinux on 2014-05-16
The first command makes sure your saucy install is fully up to date. It does not upgrade to trusty.

---

### Post by colinzealknows on 2014-05-16
> **philinux said:**
> The first command makes sure your saucy install is fully up to date. It does not upgrade to trusty.

Right. Done that, installed all packages. No errors. Still it doesn't let me do the upgrade.

---

### Post by plucky on 2014-05-16
> **mozart-archilla said:**
> Right. Done that, installed all packages. No errors. Still it doesn't let me do the upgrade.

From a terminal ```
sudo do-release-upgrade
```

Does that start the upgrade?

Also check your Software Sources under the Updates tab for Release Upgrades is set for "Any Release"

Good Luck

---

### Post by colinzealknows on 2014-05-16
Thanks plucky for providing that screenshot. I had all four checkboxes marked, unchecking the two last ones made the upgrade option finally show up.

---

### Post by philinux on 2014-05-17
You can safely enable the backports tick box. They are normally enabled by default on a clean install.

---

