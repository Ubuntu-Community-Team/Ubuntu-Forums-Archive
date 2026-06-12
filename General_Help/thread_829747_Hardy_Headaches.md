---
title: "Hardy Headaches"
date: 2008-06-15
forum: General Help
---

### Post by gingermark on 2008-06-15
Right, this is my first post in almost two years, I almost put it in the beginner's section, but thought better of it.
 
I've been without an internet connection on my Linux box for 20 months, so have been running Dapper all that time. All my hardware was purchased around the release of Breezy, and wasn't that new then. By the release of Dapper it was all automatically detected - just had to install the nvidia driver for my GeForce 6100 and that was it. 
 
After a fresh install of Hardy (KDE 3.5.9 Version) from the alternate install CD I am having a few problems that are inhibiting the use of my computer, to put it mildly. 
 
1) The X-Server stops working (ie starting up Kubuntu freezes on a black screen as soon as it trys to start X) if I install the proprietary driver from K-Menu --> System --> Hardware Drivers Manager, or indeed if I install the NVIDIA-Linux-x86-173.14.05-pkg1.run file from the Nvidia site. So I am stuck with a resolution of 600*800 using the /etc/X11/xorg.conf.failsafe file. 
 
2) Sound does not work from any application using the xine engine, which is most things for me. No sound in Amarok or Kaffeine or (shockingly) Xine-ui. VLC works through the "Default" output module, and I get sound when I "test" it in Kcontrol / System Settings
 
3) Drive mounting seems to be problematic - in Dolphin File Manager I have been asked to enter my password just to mount my other hardrives - which doesn't 'feel' right. Is that normal these days?

Also, my USB hardrive does not automount when I plug it in (I can see the workaround is listed [here]("http://ubuntuforums.org/showpost.php?p=4916614&postcount=13") but I'll be damned if I can understand it).

Any help would be very much appreciated, am happy to provide additional info if required. I have activated the Mediabuntu repository if that makes a difference...

Thank you.

---

### Post by editrix on 2008-06-15
I feel your pain :-(

We're in almost the same boat--2 years of perfect Dapper, then ...

First off, I'd check here:[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu) because some of what they talk about sounds like some of your problems.

I'll assume you have internet now. I've been searching Launchpad for reported bugs but my problems are different from yours, so ...

> just had to install the nvidia driver for my GeForce 6100 and that was it. 

Apparently, there's at least one bug about nvidia drivers. Don't know enough about them to say more. Did you check the Known Hardy Bugs and Workarounds sticky?

> in Dolphin File Manager I have been asked to enter my password just to mount my other hardrives - which doesn't 'feel' right. Is that normal these days?

Not from Konqueror. I spent about 5 minutes with Dolphin then setup my Konq the way it used to be (2 profiles, icons for each in system tray). But apparently there's Dolphin and D3lphin, and there's a difference ... Don't understand it.

But IIRC, when I mounted a memory stick it just gave me that What Do You Want to Do dialogue, and when I said Open in New Window it gave me Dolphin, no password problems.

---

