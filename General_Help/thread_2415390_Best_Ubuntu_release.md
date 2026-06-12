---
title: "Best Ubuntu release"
date: 2019-03-25
forum: General Help
---

### Post by jayhawker2 on 2019-03-25
Please, which is the best Ubuntu release for the following mini computer specs? [h=1]Intel Atom X5-Z8350, 4GB + 64GB.[/h]

---

### Post by Autodave on 2019-03-25
They all are!  Seriously, it all depends on you and what you like and what you can deal comfortably with.  My suggestion would be to download several of them and run them from an install medium on a USB stick and see what one(s) you like.  Ubuntu and Kubuntu are the fanciest desktops, but also the most memory hungry. Xubuntu, Budgie have simpler desktops that leave more memory for running programs.  

Personally, I never cared about what the desktop looked like because I don't sit here staring at it all day!  To each his own.  

Download and try a bunch of them!

---

### Post by jayhawker2 on 2019-03-25
THanks, but Xubuntu needs more than 4Gb RAM, needn't it? On the page, it is said: **Your processor**[COLOR=#333333][FONT=Noto Sans] needs to [/FONT][/COLOR]**support PAE**[COLOR=#333333][FONT=Noto Sans] in order to run Xubuntu.[/FONT][/COLOR]

---

### Post by Impavidus on 2019-03-25
Just make sure it's a supported release. 14.04 only has a few weeks of support left, so that's no option. Pick 16.04 LTS (2 years of support left for Ubuntu, but only a few weeks for the other flavours), or 18.04 LTS (the latest LTS release, 4 years of support left for Ubuntu, 2 years for the other flavours), or 18.10 (latest release, but only 4 months of support left). Best would probably be 18.04, unless (like me) you don't mind regular release upgrades or fresh installs. And with 4GiB memory I suggest 64 bit, although it doesn't matter too much (unless you want to install Chrome).

As for the flavour, you can just pick the one you like most. That computer should be able to run every flavour.

> **jayhawker2 said:**
> THanks, but Xubuntu needs more than 4Gb RAM, needn't it? On the page, it is said: **Your processor**[COLOR=#333333][FONT=Noto Sans] needs to [/FONT][/COLOR]**support PAE**[COLOR=#333333][FONT=Noto Sans] in order to run Xubuntu.[/FONT][/COLOR]

Not really. Xubuntu was the last Ubuntu flavour to support the non-pae kernel (in Xubuntu 12.04, end-of-life in 4-2015). Since then there's no longer a non-pae kernel in de Ubuntu repositories. That shouldn't be a problem. Most CPUs from the past 20 years support PAE. PAE is a trick to support more than 4GiB memory on a 32 bit system, but it doesn't mean you need more than 4GiB of memory. You can run Xubuntu quite well in 2GiB. Even in 1GiB, if you don't open too many tabs in your web browser.

---

### Post by jayhawker2 on 2019-03-25
OK. Thanks

Please, how to download from a pen drive? I see only ISO.

---

### Post by Autodave on 2019-03-25
An .iso file is an installation file.  You need to install that file onto a USB, not merely copy it onto the drive. *Unetbootin *will work for doing that.  You will have to download and install Unetbootin to create your pendrive installation.

---

### Post by jayhawker2 on 2019-03-25
Sorry, how I get this Unetbootin. Is there any guidance page?

---

### Post by speartip on 2019-03-25
I don't think Unetbootin is in the official repos anymore.
But before that, are you creating your installation medium from within a Linux or Windows operating system?

---

### Post by jayhawker2 on 2019-03-25
It is a new computer with Windows 10.

---

### Post by speartip on 2019-03-25
From within windows you probably need to use a program like Rufus to burn your iso image to a usb stick.
[https://rufus.ie/](https://rufus.ie/)

---

