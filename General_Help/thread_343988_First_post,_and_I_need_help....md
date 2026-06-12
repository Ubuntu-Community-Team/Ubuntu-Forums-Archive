---
title: "First post, and I need help..."
date: 2007-01-22
forum: General Help
---

### Post by oceanspray on 2007-01-22
Lifelong Windows user but am planning the big transition. The big escape :)   I do have a problem however and would appreciate it a lot if anyone could help me!  I downloaded the DVD version of the Edgy release, installed it fine on my Dell Dimension but though am real pleased with the quality of the font, I am really not about the GAMMA settings as I like to adjust them just so...now the colors on my desktop look washed out and the settings on my lcd monitor don't help. On my Windows system I always adjusted the settings using the Catalist driver software from ATI (have two ATI graphic cards).  Is there any application or settings I can change in Ubuntu to adjust the gamma (and color) settings?   I tried download the new ATI driver Linux, but after trying many times, I just couldn't get it installed.

Please help, thank you kindly :)

Robert

---

### Post by daemonoid on 2007-01-22
I've not done it myself as the colours have always seemed fine to me, but take a look at this:

[http://applications.linux.com/article.pl?sid=05/02/07/2244242](http://applications.linux.com/article.pl?sid=05/02/07/2244242)

It does mean a bit of hand editing config files so someone else may know of an easier gui type way.

---

### Post by CowzRule on 2007-01-22
I don't have any experience with this, but there's something called "xgamma". Open a terminal and type```
xgamma --help
```And here's a link to some help on getting those ati drivers installed
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

---

### Post by jelkimantis on 2007-01-22
> **oceanspray said:**
> Lifelong Windows user but am planning the big transition. The big escape :)   I do have a problem however and would appreciate it a lot if anyone could help me!  I downloaded the DVD version of the Edgy release, installed it fine on my Dell Dimension but though am real pleased with the quality of the font, I am really not about the GAMMA settings as I like to adjust them just so...now the colors on my desktop look washed out and the settings on my lcd monitor don't help. On my Windows system I always adjusted the settings using the Catalist driver software from ATI (have two ATI graphic cards).  Is there any application or settings I can change in Ubuntu to adjust the gamma (and color) settings?   I tried download the new ATI driver Linux, but after trying many times, I just couldn't get it installed.

Please help, thank you kindly :)

Robert

Welcome to the world of linux!  If you're not already, I would encourage you to listen to a few Linux Podcasts (Linux Reality is a good one for new Linux users).

I assume you are using Gnome with your system, but I do not know what you are planning to do.  A lot of people like the KDE destop, which has a Display Configuration tool you might find helpful.  There is some information on this at:

[https://wiki.kubuntu.org/EdgyEft/Knot3/Kubuntu](https://wiki.kubuntu.org/EdgyEft/Knot3/Kubuntu)

Some people have reported an increase in performance installing up-to-date ATI linux drivers.  It did not help my system (I had no 3D after I installed them).  You might find that you get a better picture with the ATI drivers.

Jelki

---

### Post by oceanspray on 2007-01-22
> **CowzRule said:**
> I don't have any experience with this, but there's something called "xgamma". Open a terminal and type```
xgamma --help
```And here's a link to some help on getting those ati drivers installed
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

I did that and got this: 
oceanspray@oceanspray-desktop:~$ xgamma --help
usage:  xgamma [-options]

where the available options are:
    -display host:dpy       or -d
    -quiet                  or -q
    -screen                 or -s
    -gamma f.f              Gamma Value
    -rgamma f.f             Red Gamma Value
    -ggamma f.f             Green Gamma Value
    -bgamma f.f             Blue Gamma Value

If no gamma is specified, returns the current setting
oceanspray@oceanspray-desktop:~$

Don't know what to change there also the explanation on the link is way over my head.  Just want to install the ATI driver, I am not a coder ;) 

Thanks!

---

### Post by oceanspray on 2007-01-22
> **jelkimantis said:**
> Welcome to the world of linux!  If you're not already, I would encourage you to listen to a few Linux Podcasts (Linux Reality is a good one for new Linux users).

I assume you are using Gnome with your system, but I do not know what you are planning to do.  A lot of people like the KDE destop, which has a Display Configuration tool you might find helpful.  There is some information on this at:

[https://wiki.kubuntu.org/EdgyEft/Knot3/Kubuntu](https://wiki.kubuntu.org/EdgyEft/Knot3/Kubuntu)

Some people have reported an increase in performance installing up-to-date ATI linux drivers.  It did not help my system (I had no 3D after I installed them).  You might find that you get a better picture with the ATI drivers.

Jelki

Thanks for the welcome and its great to see all the helping hands, one of the reasons why I choose Ubuntu!!     You assumed right (about Gnome).   On the long term I would like to migrate away completely from Windows.   Installing the ATI driver proved too difficult for me.   I am extremely unfamiliar with Linux, but you figured that out, am sure :) 

Do want to stay with Ubuntu because it seems to have the most support;

---

### Post by sloggerkhan on 2007-01-22
Try getting gxvattr from the add/remove menu.
(notice it has graphical frontend.)

I think it might only apply to movies, though.... (not sure)

KDE also has a gamma module. (kgamma)

---

### Post by CowzRule on 2007-01-22
> **oceanspray said:**
> I did that and got this: 
oceanspray@oceanspray-desktop:~$ xgamma --help
usage:  xgamma [-options]

where the available options are:
    -display host:dpy       or -d
    -quiet                  or -q
    -screen                 or -s
    -gamma f.f              Gamma Value
    -rgamma f.f             Red Gamma Value
    -ggamma f.f             Green Gamma Value
    -bgamma f.f             Blue Gamma Value

If no gamma is specified, returns the current setting
oceanspray@oceanspray-desktop:~$

Don't know what to change there also the explanation on the link is way over my head.  Just want to install the ATI driver, I am not a coder ;) 

Thanks!

Ok, I just played with this.. (f.f = some number i.e. 1.0)

displays what xgamma is set to```
xgamma
```
adjust all colors at once```
xgamma -gamma f.f
```
adjust the color red```
xgamma -rgamma f.f
```
adjust the color green```
xgamma -ggamma f.f
```
adjust the color blue```
xgamma -bgamma f.f
```
For more info about xgamma type```
man xgamma
```

---

### Post by shane634 on 2007-01-22
If all else fails with the ATI drivers you can get AutomatixBleeder to install them. Just go to getautomatix.com and install it. Then open it in Applications-->System tools-->AutomatixBleeder. And point it to the ATI driver then click start. Good luck.

---

