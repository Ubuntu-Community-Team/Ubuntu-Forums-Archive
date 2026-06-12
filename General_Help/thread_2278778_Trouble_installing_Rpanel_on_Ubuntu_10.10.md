---
title: "Trouble installing Rpanel on Ubuntu 10.10"
date: 2015-05-19
forum: General Help
---

### Post by Mantej on 2015-05-19
Dear forums,

I am relatively new to Ubuntu. I know that my system, Ubuntu 10.10, is really out-dated but as per given instructions, upgrading the OS is my last resort. I have successfully installed R (statistics programming software) on my laptop and am now attempting to download package Rpanel. However, after installing it, RStudio it seems is unable to actually detect or use it. I've been searching the internet for solutions but am unable to find one.

Apologies if this has been posted in the wrong section

---

### Post by QIII on 2015-05-19
I would absolutely recommend installing a supported release of Ubuntu.  

First:  There are substantial security risks in running an unsupported release.

Second:  The repositories for 10.10 have been moved to old-releases and you cannot update or install new software from there.  Furthermore, third party software will likely include dependencies that will not be fulfilled by such an old release.

---

### Post by Mantej on 2015-05-19
thanks for the prompt reply! just to double check, if i were to procede with upgrading my os, i would have to upgrade step-by-step 10.10>11.10>12.10>14.10?

---

### Post by QIII on 2015-05-19
That would be a recipe for disaster.  Upgrading through a series of unsupported releases is bound to fail.

I would back up all of your important files and re-install fresh.

I would also recommend installing one of the currently supported LTS (Long Term Support) releases:  12.04.5 or 14.04.2.

One caveat with either of those two:  If you are running an ATI graphics card that is still supported (HD 5000 series or later) there is a bug in the installation package as described [here]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491").  If you are not using ATI graphics, don't worry about this.  If you are using a model prior to HD 5000, you must use the default open source Radeon driver that will be installed with Ubuntu.

---

### Post by mörgæs on 2015-05-19
Since we are dealing with an installation from 2010 I guess that the graphics card (if it is AMD) is older than HD 5000. Expecting the install to proceed without problems using the default open source drivers.

---

### Post by mattharris4 on 2015-05-20
A couple of quick questions.  I ask because in version 11.04 (IIRC) Ubuntu switched from Gnome 2 to Unity as its desktop environment.  Unity requires (in my experience) at least 2.5GB of RAM to run reliably with the current version (I understand 10.04 would run on about 1GB of RAM).  I would hate to have you install Ubuntu 14.04 LTS (I would not suggest 12.04 as it will go EOL in about two years unless the later kernel in the current LTS version doesn't support your computer, 14.04 is supported for about four more years) and have a computer that can't run any faster than a turtle in a marathon.

1.  What is the make and model of your computer?

2.  How much RAM does your computer have?

3.  What CPU does your computer have?

4.  If applicable what video card does your computer have?

If you have a CPU with integrated graphics of at least a Pentium 4 3.0GHz (about a year 2006-2007 CPU), a Core 2 Duo (or Quad) of any year or a Celeron from about 2009 or later (or the AMD equivalent) and 1.5GB of RAM Lubuntu (which is a lighter Canonical OS with the same basic kernel as Ubuntu but a lighter DE and associated programs) may be the way to go.  More than likely you do not have the RAM or CPU to run a current Ubuntu version with Unity even if you bought it in 2010 and immediately installed Ubuntu 10.04 on it unless you bought it used/refurbished recently or spent big money on it new (likely over $800 if purchased new).  The higher speed Pentium 4's (3.0GHz or higher) and Core 2 Duos/Quads will run Ubuntu or Edubuntu well enough if you can upgrade your computer to at least 2.5GB of RAM, an older Celeron probably will not -- unfortunately many consumer level computers from this era had the early Celeron or even worse CPU.

Other options if you don't like Lubuntu are Xubuntu and Kubuntu, they are middle-weight OSes from Canonical that will run on 1.75GB of RAM, Ubuntu MATE (which runs a version of Gnome2 called MATE that has the current kernel) may be an option but an LTS version will not be available until May 2016.  Ubuntu Gnome runs Gnome3 as a DE but I don't know enough about it to venture a guess as to whether it is any lighter than Ubuntu with Unity.  If you are running a pre-2009 Celeron, a Pentium 3 or older or have less than 1.5GB of RAM and cannot install more it is time to look at Puppy Linux.  Puppy is not a Canonical OS and does not have Canonical-level support but is purported to run for internet or word processing on 256MB of RAM (although I would recommend 512MB just to be safe, Canonical claims Ubuntu will run on 2GB of RAM and Lubuntu on 512MB and I found those claims to be overly optimistic at best -- I have to assume Puppy's claims are similarly overly optimistic until proven otherwise).  Tiny OS is another option that claims to run on 128MB of RAM but I have absolutely no experience running it so I cannot either recommend or not recommend it.

If all of this causes you to want to just replace your computer Dell recently started selling laptops on their direct sales website with Ubuntu 14.04 on them.  They come with either new Pentium or Celeron CPUs, most with 4GB of RAM  and come in 14" or 15" versions (the 14" Celerons come with only 2GB of RAM -- not enough to run Ubuntu IME).  Pricing starts at $189 for 14" laptops (although I recommend spending the $249 for a Pentium if you go with this size), the 15" laptops start at $249 (I recommend spending the extra $30 for a Pentium here as well).  Here is a link:  [http://www.dell.com/us/p/inspiron-15-3551-laptop-ubuntu/pd?ref=PD_OC](http://www.dell.com/us/p/inspiron-15-3551-laptop-ubuntu/pd?ref=PD_OC)

---

### Post by mörgæs on 2015-05-20
The post above boils down to:
Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by Mantej on 2015-05-20
Hey buddy, really appreciate the long reply.

1) Toshiba PTME3L-00W019

2) 8gb RAM

3) Intel(R) Core(TM) i5 CPU M 520 @ 2.40GHz

4) nVidia Corporation GT218 [NVS 2100M]

Currently, I'm having issues with the re-installation of Ubuntu as I do not have a disk and my workplace doesn't have any spare external harddrives that are COMPLETELY empty for use for re-installation. Are there any alternatives to reinstallation via cd/usb? Or rather am I able to reinstall Ubuntu on a external harddrive that is not completely empty? As i've read that using a harddrive for re-installation will lead to loss of existing data. Once again, appreciate your time and effort!

Cheers

---

