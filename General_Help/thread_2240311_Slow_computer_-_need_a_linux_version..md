---
title: "Slow computer - need a linux version."
date: 2014-08-19
forum: General Help
---

### Post by david228 on 2014-08-19
I have recently been given an old laptop, a Pryon MS-1314, that came with a rather unstable version ov Vista.

I installed my copy of Ubuntu 14.04, and while it installed, it was so absolutely slow.

Is there a basic Linux version that anyone could recomend that is still available that would breathe back life into the old laptop?

---

### Post by slickymaster on 2014-08-19
Can you update your question , how much ram do you have? If you want the fastest "out of the box" performance, try Lubuntu.

Your other option might be a minimal install and build up, depends a bit on your RAM. Please have a read at [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) and [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by david228 on 2014-08-19
It has 1 G of RAM, pretty basic really.

It would just seem a shame to park it at the back of the cupboard till one day it's thrown out.

---

### Post by slickymaster on 2014-08-19
If I were you I would start here: [http://distrowatch.com/search.php?category=Old+Computers]("https://help.ubuntu.com/community/Lubuntu-fake-PAE")

---

### Post by yancek on 2014-08-19
You should certainly be able to run Lubuntu on your system, probably some other Ubuntu derivatives also but not the likes of Mint or Zorin.  Another non-Ubuntu which should have no problems is antiX.

---

### Post by Al1000 on 2014-08-19
The fastest, lightest Linux OS I have ever used is Puppy. I have [Lucid Puppy 5.2.8.6]("http://www.murga-linux.com/puppy/viewtopic.php?t=90461") installed on my old laptop, along with Kubuntu 12.04 as a dual boot system.

---

### Post by stalkingwolf on 2014-08-19
i run mint 13 on a system that has only 1gb of ram and it runs fine.

---

### Post by oldfred on 2014-08-19
If you installed full Ubuntu then Unity is the issue. That requires both more RAM and a newer video card or chip.

Either Xubuntu or Lubuntu should run well on that system.
       xubuntu-desktop (the whole xfce4 environment)
lubuntu-desktop (the whole LXDE desktop environment)
    
 If you do not like Unity, use K/L/X ubuntu or the DE/ WM of your choice. 
Difference between Windows manager & desktop enviroments
[http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893](http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893)

I have 12.04 on my old laptop with 1.5GB of RAM. But it will not run Unity but does run fallback well. I have not tried 14.04's version with gnome-panel on it.
      
 sudo apt-get install gnome-panel
On login screen click on logo/cog-wheel/star and choose 
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)


 [https://wiki.gnome.org/action/show/Projects/GnomeFlashback?action=show&redirect=GnomeFlashback](https://wiki.gnome.org/action/show/Projects/GnomeFlashback?action=show&redirect=GnomeFlashback)
[http://www.omgubuntu.co.uk/2014/04/ubuntu-14-04-classic-gnome-flashback-session](http://www.omgubuntu.co.uk/2014/04/ubuntu-14-04-classic-gnome-flashback-session)
Flashback/fallback in 14.04 Kansasnoob
Installing the package 'gnome-session-flashback' does exactly the same thing as installing the package 'gnome-panel'.
[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)
[http://ubuntuforums.org/showthread.php?t=2090021&p=12994477#post12994477](http://ubuntuforums.org/showthread.php?t=2090021&p=12994477#post12994477)
[http://ubuntuforums.org/showthread.php?t=2184682&p=12986002#post12986002](http://ubuntuforums.org/showthread.php?t=2184682&p=12986002#post12986002)
[http://ubuntuforums.org/showthread.php?t=2184682&p=12971487#post12971487](http://ubuntuforums.org/showthread.php?t=2184682&p=12971487#post12971487)

---

### Post by Ksiencha on 2014-08-20
I personally use Linux Mint 17 Mate edition on my old laptop (also 1GB RAM), it's decent for me. :) Tried Ubuntu 14.04 before, but it was very slow either.

---

### Post by stalkingwolf on 2014-08-20
havent tried 17 yet

---

### Post by GoPool on 2014-08-20
I've started a blog detailing my experience running Xubuntu 14.04 on a 10-year old IBM Thinkpad. See [here]("http://tplinux.blogspot.com/"). You should check it out. I'm learning about new ways to squeeze performance out of legacy hardware all the time.

---

### Post by Dragonbite on 2014-08-20
> **GoPool said:**
> I've started a blog detailing my experience running Xubuntu 14.04 on a 10-year old IBM Thinkpad. See [here]("http://tplinux.blogspot.com/"). You should check it out. I'm learning about new ways to squeeze performance out of legacy hardware all the time.

My 10 year old IBM thinkpad (not Lenovo, IBM..) wasn't able to run Ubuntu (PAE-kernel issue) so I ran openSUSE w/KDE on it and it ran great!  The performance was noticeable on larger projects and applications but not like it was dead-in-the-water.  Unfortunately the T40's screen's backlight failed and it is now forced to be tethered to a monitor.

I have an old Gateway Netbook my brother gave me, which I installed Ubuntu 14.04 on it and man that was a dog (slow).  It also does not like Gnome-shell with any distribution.  So currently it is running Fedora w/Xfce because Xubuntu and Ubuntu kept running the fan all of the time while Fedora doesn't immediately.

---

