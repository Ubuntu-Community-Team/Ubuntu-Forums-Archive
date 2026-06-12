---
title: "wacom bamboo tablet"
date: 2012-11-25
forum: General Help
---

### Post by chuning on 2012-11-25
hello - 

I have just bought a Wacom Bamboo CTL-470, am using 12.04, and cannot get it to work.  I have trawled around google, and followed various solutions that I found, but it does not work.  I have tried it on my windows netbook, and it works fine, but not in ubuntu.  

Can anyone help?

Many thanks

Chris

---

### Post by -ijk- on 2012-11-25
Upgrade to 12.10 - it includes drivers for this.

---

### Post by Favux on 2012-11-25
Hi chuning,

You would need to compile at least input-wacom to get the tablet working in Precise (12.04).  See the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  Or the [updated version]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110408&sid=4c93c8b9d73e237087d2d42a38f548a5").  You could also use [Lekensteyn's PPA]("https://launchpad.net/~lekensteyn/+archive/wacom-tablet"), although it uses input-wacom-0.13.0 and input-wacom is now up to 0.15.0, it should still work.

However if you also decide to update xf86-input-wacom you'll need to apply the [frankenserver patch]("http://ubuntuforums.org/showpost.php?p=12146782&postcount=1034") to it before compiling.

---

### Post by chuning on 2012-11-25
Thanks for that.  I've tried downloading the PPA, but it doesn't seem to download - when I try to install it it says it cannot find the package.  I'm not very experienced with this, so am quite possibly doing something stupidly wrong

---

### Post by Favux on 2012-11-25
That could be because I know it installs on Precise.  When you say:
>  I've tried downloading the PPA, but it doesn't seem to download - when I try to install it it says it cannot find the package.
Did you actually download something?  Or did you follow the PPA installation instructions in "Adding this PPA to your system" for Software Sources or through the terminal (Read about installing)?

---

### Post by chuning on 2012-11-25
i followed the instructions in "adding this ppa to your system"

---

### Post by Favux on 2012-11-25
Huh.  Do you have vanilla Precise Unity?  Do you now see the PPA in Update Manager's Settings under the "Other Software" tab?   Or maybe Launchpad was having some troubles.

---

