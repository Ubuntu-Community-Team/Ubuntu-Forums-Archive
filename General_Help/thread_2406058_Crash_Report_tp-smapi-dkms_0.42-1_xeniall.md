---
title: "Crash Report tp-smapi-dkms 0.42-1 xeniall"
date: 2018-11-15
forum: General Help
---

### Post by simon114 on 2018-11-15
Good morning, 

as the heading implies when I'm doing an update i get this as a crash report, then im told it cant be reported as its not an official package. I've looked it up, and found that its thinkpad software, Wierd as I have a toshiba...Can someone please tell me 
1)what this package is and what its for.
2)If its needed
3)how to update or remove it to avoid further crash reports. 

Thanks community.

---

### Post by slickymaster on 2018-11-15
Have a read at [https://packages.debian.org/stable/tp-smapi-dkms](https://packages.debian.org/stable/tp-smapi-dkms) regarding the package

There's a new version of that package available: [https://tracker.debian.org/pkg/tp-smapi](https://tracker.debian.org/pkg/tp-smapi)

---

### Post by simon114 on 2018-11-15
Hi slickymaster,

Do i need this package? if not how do I remove it, If yes, which version would you suggest (0.42-1?)and how do I update it, Thank you


[LIST]
[*]o-o-stable: [0.41-1]("https://packages.debian.org/source/oldoldstable/tp-smapi")
[*]oldstable: [0.41-1]("https://packages.debian.org/source/oldstable/tp-smapi")
[*]stable: [0.42-1]("https://packages.debian.org/source/stable/tp-smapi")
[*]stable-bpo: [0.43-1~bpo9+1]("https://packages.debian.org/source/stretch-backports/tp-smapi")
[*]testing: [0.43-1]("https://packages.debian.org/source/testing/tp-smapi")
[*]unstable: [0.43-1]("https://packages.debian.org/source/unstable/tp-smapi")
[/LIST]

---

### Post by slickymaster on 2018-11-15
I strongly desavise the removal. Its main implemented functionality is the control of battery charging and extended battery status and also includes an improved version of the HDAPS driver.

The existing package for Xenial is **tp-smapi-dkms (0.41-1)**, not 0.42-1ubuntu1, so either you [downgrade]("https://askubuntu.com/questions/138284/how-to-downgrade-a-package-via-apt-get") or [fill a bug]("https://launchpad.net/ubuntu/+source/tp-smapi/+bugs") regarding the version you have installed.

---

