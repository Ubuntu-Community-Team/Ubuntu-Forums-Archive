---
title: "Old versions vs. New"
date: 2013-02-07
forum: General Help
---

### Post by bigbankclub on 2013-02-07
What risks does one have running version 
[B]
Ubuntu 8.04 LTS (Hardy Heron) 
[/B]
[B]vs 
[/B]
**Ubuntu 12.10 (Quantal Quetzal)**

I understand we are talking years apart. But what issues could one have? I'm running a copy of Ubuntu 8.04 LTS and finding it much smoother than the newer one. As for updates I manged to edit /etc/apt/sources.list and get the Synaptic Package Manager to update. That was nice.

I'm not running any servers, just a development environment. Any risks that I may run?:o

The Update Manager just opened and YIKES a whole 388 updates. That will take forever on my dial-up .. hahaha just kidding about the dial-up.But seems very smooth!! Nice!!!

---

### Post by sudodus on 2013-02-07
The end of life of Ubuntu 8.04 LTS desktop was April 2011. After that it has only received security updates for the packages that also belong to the server edition. I think it is a bad idea to run the 8.04 LTS desktop version, when connected to the internet.

Instead I recommend that you make a fresh install of Ubuntu 12.04 LTS with support until April 2017, or Xubuntu 12.04 LTS with support until April 2015. Xubuntu has a lighter desktop environment, XFCE, and runs smoothly also in aging computers.

This way you will also receive a lot of improved software and recognition of new hardware including peripheral devices. It is OK to try 12.10, but it is not yet as debugged and stable as 12.04, and there are also problems to run some older hardware.

---

### Post by kurt18947 on 2013-02-07
I agree that 12.04>12.10.  There are a number of 'flavors' of 12.04 - Ubuntu, Xubuntu, Lubuntu, gnome(shell) Mint 13 and on and on.  You're not 'stuck' with Unity although Unity is not as bad as everyone says, just a lot different.  Unity & gnome-shell are not good choices on older machines or those with weak graphics systems.

---

### Post by Mark Phelps on 2013-02-07
> **bigbankclub said:**
> What risks does one have running version 
[B]
Ubuntu 8.04 LTS (Hardy Heron) 
[/B]
[B]vs 
[/B]
**Ubuntu 12.10 (Quantal Quetzal)**

I understand we are talking years apart. But what issues could one have? 

Well, for one, kernel changes.  I had an old Tablet PC that worked GREAT under 8.04 -- and never worked well again in ANY of the releases after that.  Seems the newer kernels could just not see some of the special hardware on the device -- hardware that I needed to use on a daily basis.

Then, there's the default desktop changes.  Current versions some with Unity -- which if you like "smarphone-like desktops", you will like.  But, Unity places strong demands on graphics, and if your video chipset isn't up to it, unlike with older versions, there is no Unity 2D you can use.

There's also X-Server version upgrades.  AMD dropped Linux driver support for their (still being sold!) HD 2x/3x/4x series chipsets this last summer.  IF you have one of these, you can't install the AMD restricted drivers in Ubuntu 12.10 because the drivers compatible with these (now "legacy") cards will not work with the newer X-server version resident in Ubuntu 12.10.

---

### Post by bigbankclub on 2013-02-07
Got updates to work but not for that version.

Yes I agree security issues, but I don't do updates on Windows or run any virus protection. No issues and as for Unity or changing to Gnome, it still does not feel like 8.10. 

I find 8.10 is smoother and hey I could stay offline to avoid some risk and just use it as development machine regardless. But I truly feel and see the difference from over the years.

Thanks guys! I'm testing 4.10 now. Not expecting much; but just worth a try!:D

---

### Post by sudodus on 2013-02-07
Please post data about your computer, at least cpu, ram and graphics chip/card, so that we can give better advice!

---

### Post by bigbankclub on 2013-02-07
XP Service Pack 3

i7-2600k @ 3.40 GHz
3.41 GHz, 16GB Ram

---

### Post by grahammechanical on 2013-02-07
Is the machine still working? Is the OS still working? What's the problem? This is the last 8.04 security update recorded in the Ubuntu Weekly Newsletter

[https://lists.ubuntu.com/archives/hardy-changes/2013-January/012867.html]("https://lists.ubuntu.com/archives/hardy-changes/2013-January/012867.html")

Does it mean anything to you? No? Nor me. How relevant are these security fixes to the ordinary users anyway? Well, you will not be getting any of them any more. If it does not trouble you, then do not let it trouble you. Just do not try to upgrade to newer versions of applications.

New releases of Ubuntu keep up to date with newer hardware. 7.04 worked well on my machine. Five years later 13.04 is working well on it. The hardware is still the same. Do I really need to run the very latest Ubuntu? It is my choice.

Regards.

---

### Post by sudodus on 2013-02-07
> **bigbankclub said:**
> XP Service Pack 3

i7-2600k @ 3.40 GHz
3.41 GHz, 16GB Ram

Every new version and flavour of Ubuntu should run well with that computer.  So you can give priority to eye-candy or speed, new features or stability, security updates or old well-known software.

I think that Ubuntu 8.04 and 8.10 are too old to really understand all the new features of your computer.

It might be an option to install more than one system, ***dual boot or multi boot***, to evaluate or simply use each system, where it is the best.

---

### Post by snowpine on 2013-02-07
Maybe give [Fuduntu]("http://www.fuduntu.org/") a try? Fuduntu has the old-style Gnome 2 desktop that will remind you a bit of 8.04, but updated for 2013. It's slick. :)

---

