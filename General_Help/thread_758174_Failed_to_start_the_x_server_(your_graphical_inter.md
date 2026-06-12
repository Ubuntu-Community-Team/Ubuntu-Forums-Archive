---
title: "Failed to start the x server (your graphical interface)..."
date: 2008-04-17
forum: General Help
---

### Post by Burmie on 2008-04-17
I always wanted to switch to linux, but everytime i try theres always a hitch. I really really want to get this Ubuntu running. I have Ubuntu 6.10 (edgy eft) on a live cd that i picked up with "Beginning Ubuntu Linux". I built a new computer that i was planning to dual boot xp and ubuntu with. But when i booted up with the live cd i got this
"
Failed to start the X server (your graphical interface). It is likely that it is not set up up correctly. Would You like to view the x server output to diagnose the problem?"
i click yes and i get:
"X window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux ubuntu 2.6.17-10-generic #2 SMP Fri Oct 13 18:35:35 TUC 2006 i686
Build Date 07 July 2006
Before Reporting problems, check [http://wiki.x.org](http://wiki.x.org)
to make sure you have the latest version
Modular Loader present
Markers: (--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log File: "/var/log/Xorg.0.log", Time: Thu Apr 17 18:20:27 2008
(==) Using config file: "/etc/X11/xorg.conf" 
"
i click ok
i then get "would you like to view the detailed x server output as well?"
i click yes
i get the same thing as before "X window system Version..."

I have a Windows XP Pro Machine (runs flawlessly). Asus M2N-SLI Delux Mobo, AMD 64 X2 5600+ Dual Core Processor, 2x 1 gb Corsair XMS memory and 2x 512 mb (3gb total), NVIDIA GeForce 8500 GT video card. This is the machine i want to dual boot it on.
Thanks for your time. I want to give linux one more chance.

---

### Post by sekinto on 2008-04-17
Why would you want to install Edgy when [Hardy]("http://www.ubuntu.com/") is comming out in a week?

You are a few releases behind:
_Edgy_
Fiesty
**Gusty**
Hardy

Currently two, in a week you would be three releases behind the current stable release of Ubuntu.
I would suggest either downloading a Gusty or a Hardy Live CD.

If you really still want to just install Edgy I would try some of the alternate boot options.

---

### Post by aktiwers on 2008-04-17
I would also try a newer version. It could very well be your videocard or something. And your videocard is supported in later versions.

So.. Power your XP computer, download the latest ubuntu (gutsy), Herdy is ready in 1 week though, and burn the Iso as Image slowly. 

Then boot it and you have a better change to succeed ! :)

---

### Post by Burmie on 2008-04-17
I know the version is old, but i cant even boot up live cd mode. it's very discouraging. i still want to make some headway though, even if it is to just get to the desktop in live cd mode. 
also i ran out of blank cds XD

---

### Post by aktiwers on 2008-04-17
Does it trow you to terminal then?
Then you can type this:
```
sudo /etc/init.d/gdm stop
```

```
sudo dpkg-reconfigure xserver-xorg
```And follow the onscreen stuff.. if you don't know what to do pick the default.(hit enter)

Then:
```
startx
```I think that would work.

But it's easier to download a newer version I guess.

---

### Post by Burmie on 2008-04-18
i will try that and get back to you and tell you how it comes out.
thank you.

---

### Post by doorknob60 on 2008-04-18
If I were you, I would go download the Hardy beta (not worth downloading Gusty this late because you'll have to download another 700+ Mb when you upgrade in a week, if you do). You can get it here: [http://www.ubuntu.com/testing/hardy/beta](http://www.ubuntu.com/testing/hardy/beta)

In Gusty and higher (from my experiences), instead of givven an X error, it puts you in safe graphics mode which has crappy quality graphics but you can still do stuff. In Feisty (which is newer than Edgy), it gave that error, but it didn't in Gusty and Hardy.

---

### Post by ad_267 on 2008-04-18
> I know the version is old, but i cant even boot up live cd mode. it's very discouraging. i still want to make some headway though, even if it is to just get to the desktop in live cd mode.
also i ran out of blank cds XD

The newer versions don't just add new features, they provide better support for hardware, so using a newer version (Gutsy or Hardy) would be very likely to fix this problem.

---

