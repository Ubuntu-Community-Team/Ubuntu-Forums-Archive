---
title: "Lenovo T410S, Moving from LM17Cinnamon 64 Bit to Ubuntu14.04LTS 64bit"
date: 2014-09-11
forum: General Help
---

### Post by SJLPHI on 2014-09-11
Hello, I will first say that I am moving to Ubuntu 14.04 from LM17. I am currently installing the distro on my laptop and noticing the difference in the desktop environment.

My laptop is Lenovo T410S, and I have tried to get this computer to work well and have done some tweaks here and there. I've had a couple of systematic failure in the past month and decided to move to a more popular distro. Most fatal failure about an hour ago.

 I have to admit I miss the Windows7-similar-desktop environment which that LM17 Cinnamon offered.

This is the list of the things that I am going to install in order
ROOT
Python2&3+Scipy+Numpy+ipython
TeXmaker
TLP
ThinkFan
Crossover<=MS Office 2010 (LibreOffice is simply incompatible with native excel & imported docs)
Clamav/TK
RKhunter
Chkrootkit

The top 5 are my "essentials"

This is actually an unresolved issue from LM17:
[http://forums.linuxmint.com/viewtopic.php?f=49&t=173213](http://forums.linuxmint.com/viewtopic.php?f=49&t=173213)

I hope I don't bump into it here.

This is what I'm going to Apply, once the system is up and stable. Obviously my directions were taken from Ubuntu support, I'm sure that I'll have no problems with it.
[http://forums.linuxmint.com/viewtopic.php?f=46&t=176542](http://forums.linuxmint.com/viewtopic.php?f=46&t=176542)

I did a search in the forums and I didn't find anyone mentioning my laptop model. (There were some on google search who said they had Ubuntu, but 12, not 14)

First: I would like to ask if anyone has Lenovo T410 or T410S to send me any tips/warnings that I should be aware about.
Second: I've only used Ubuntu once before and I am not very familiar and I'm sure I'll find my way around most but please let me know if you have any optimization tips.

Thank you
-SJL

---

### Post by Bucky Ball on 2014-09-12
*Thread moved to **General Help**.*

Welcome. If you want Windows-like, why not try Xubuntu or Lubuntu? Xubuntu is extremely configurable and more lightweight than Ubuntu. 

As for optimisation tips, I always do minimal installs, use xfce4 as the desktop environment, and only install apps that I want/need. That way I don't get a heap of default apps I have no use for and will never need.

Unsure what you mean by 'optimisation' tips. Things that make the machine go faster? How to unclutter the desktop? It's not the same as Windows and there isn't much need to go through an arm's length of optimisation tweaks to get things running smoothly.

---

### Post by SJLPHI on 2014-09-12
Lubuntu is not compatible with many of the things that I need.
Also, I found at least in LM17 many tweaks and problems were machine-specific. My computer has 2.6Ghz i5 dual core and 8GB ram, which can handle everything quite well, I still want to make it run as fast as it can.

What I mean by optimization has two purposes :
1.Speeds up boot
2.More stable system.

---

### Post by SJLPHI on 2014-09-12
My system is now relatively stable
 and 
[COLOR=#000000]"This is what I'm going to Apply, once the system is up and stable. Obviously my directions were taken from Ubuntu support, I'm sure that I'll have no problems with it.[/COLOR]
[http://forums.linuxmint.com/viewtopic.php?f=46&t=176542](http://forums.linuxmint.com/viewtopic.php?f=46&t=176542)"

is not working for some reason. The gnome lock works independently but it does not load after boot. Any input?

---

### Post by Bucky Ball on 2014-09-12
> **SJLPHI said:**
> ... I still want to make it run as fast as it can.

What I mean by optimization has two purposes :
1.Speeds up boot
2.More stable system.

I have an i3 with 4Gb of RAM and I run, and would advise you to try, a minimal install. Less moving parts means faster and more stable.

Minimal Install page:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Older, but info still relevant while screenshots might be a bit different now:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

If you're up for it, experiment with it on a spare partition or drive, but I'd say look around a bit first and try a few things so you can install just the things you want.

---

### Post by SJLPHI on 2014-09-12
Hey Thank you but I think I'll stick around with Ubuntu 14.04 LTS at the moment. I am finding the distro very stable and compatible. It certainly is different from LM17 Cinnamon but I think I am finding my way around it Currently all the hardware specific issues that I've had with LM17 are gone.

Earlier today, I broke Ubuntu by trying to install tweakers and other desktop environments and purging what I thought were non-essentials.
I've re-installed the distro fresh and this time partitioned boot, swap and root myself. 1GB, 2GB and the rest with respect.

I am currently in process of re-installing everything that I call essentials. So far so good.

---

### Post by SJLPHI on 2014-09-13
It seems that I spoke a little too soon. It's the second time I've installed Ubuntu 14.04 LTS, and both times when I do update, upgrade and dist-upgrade, at some point the OS becomes broken.

First sign is when the network applet disappears and the second is constant bug messages then lastly sluggish slowing down keyboard and I can't even do anything with it...

---

### Post by Rob Sayer on 2014-09-13
First off, Mint is actually based on Ubuntu.  It uses an older version of the kernel but otherwise it's the same underneath.  

So installing ubuntu thinking you're going to fix a mint problem isn't likely to work.  However, Mint tech support is not good.  There aren't any distros that have tech support anywhere nearly as good as ubuntu except for some that are definitely *not* noob friendly.

You'd probably be better off posting a thread here re your original mint issue.  You'll need to post a lot more info, and also hardware details.

Also, don't expect kubuntu to work any better than any other DE version of ubuntu if it's an underlying hardware config issue.  That's handled the same in all ubuntu flavors.  One of the things that new linux users don't get often is that as far as linux is concerned, the DE (cinnamon or KDE or whatever) is *just another application program* as far as the OS goes.  This goes for everything above kernel level.  In fact to say that "Lubuntu is not compatible with many of the things that I need" really doesn't make much sense.

---

### Post by SJLPHI on 2014-09-13
Well, I think and I hope the third time is charm. It is so far stable and it is up to 95% of everything that I used to have

---

