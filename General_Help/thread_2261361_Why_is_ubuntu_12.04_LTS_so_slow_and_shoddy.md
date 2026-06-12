---
title: "Why is ubuntu 12.04 LTS so slow and shoddy?"
date: 2015-01-18
forum: General Help
---

### Post by user_linux on 2015-01-18
For years Ubuntu was so fast, but now sad to say even windows is faster than ubuntu. I use Chrome and from time to time, the screen freezes and not responds and takes a while to get back active. Also sometimes when it remains idle and I have to enter my login details to enter in the system, login window appears after a while and takes a while to load my screens. Why is such inconsistency, I mean sometimes ok but sometimes not?

Thanks.

---

### Post by TheFu on 2015-01-18
What do the log files say?
Without any real data or facts, we can only guess there is a hardware issue that isn't a complete failure, yet.
The easiest way I know (besides looking at log files) to test is to boot off a liveCD and see if it is still slow in the same way or not.

---

### Post by user_linux on 2015-01-18
> **TheFu said:**
> What do the log files say?
Without any real data or facts, we can only guess there is a hardware issue that isn't a complete failure, yet.
The easiest way I know (besides looking at log files) to test is to boot off a liveCD and see if it is still slow in the same way or not.

How do I create a log file?

---

### Post by deadflowr on 2015-01-18
> **user_linux said:**
> How do I create a log file?

You have a folder already dedicated to log files.
It's in /var/log.

12.04 also includes a quick user-ready program called log viewer which output several of the more common log files.
usually graphical glitching is an xorg thing, so probably look over that one, as a start.

---

### Post by TheFu on 2015-01-18
[http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files) is another way to review log files for issues. Much faster than scrolling through thousands of lines of logs in 20+ different files.

---

### Post by kerry_s on 2015-01-18
> **user_linux said:**
> For years Ubuntu was so fast, but now sad to say even windows is faster than ubuntu. I use Chrome and from time to time, the screen freezes and not responds and takes a while to get back active. Also sometimes when it remains idle and I have to enter my login details to enter in the system, login window appears after a while and takes a while to load my screens. Why is such inconsistency, I mean sometimes ok but sometimes not?

Thanks.

i find elementary os to be the fastest distro built on ubuntu 12 lts. ubuntu always seems to have that kind of slowness to it, click something, wait a bit, like its thinking about what i just did & what to do.

---

### Post by TheFu on 2015-01-18
> **kerry_s said:**
> i find elementary os to be the fastest distro built on ubuntu 12 lts. ubuntu always seems to have that kind of slowness to it, click something, wait a bit, like its thinking about what i just did & what to do.

I agree that a lighter GUI will make Ubuntu faster.  Most of the issue is with Unity, IMHO.  However, switching to a different distro just to have a different GUI seems excessive. GUIs are NOT the OS. In Linux, the GUI is just another program to be loaded, used or removed.  There must be 50 alternative GUIs and pretty much **any** of these will be faster than Unity without fail.

[Here are some of the most popular]("http://askubuntu.com/questions/65083/what-kinds-of-desktop-environments-and-shells-are-available") (with screenshots).

We are all a little different.  Back in 2010, I created a tiny customization for LXDE for my 80 yr old Mom to use that had the 5 things she wanted on the left side of the screen ... like the Unity appearance, but not at all that heavy or slow. Plus it wasn't sending anything Mom searched for to external parties (like Amazon), so it was FAST.  I know this to be true - Mom had a P4 with 1G of RAM, but when her motherboard failed, we swapped in a Core i7 with 6G of RAM. She didn't notice - because the outside of the box didn't look any different and everything was exactly the same.  I prodded her to say it was fast and eventually, she agreed, but I think she was just being nice.  LXDE is fast on most hardware still running today.  XFCE is also popular on lower-end hardware.

If these are too heavy, it is always possible to dump a DE completely and go old school with a pure WM (window manager) environment. Every DE is running a WM already, so these are well maintained, unless you do like me and try one from the mid-1990s out of nostalgia. BTW, fvwm still rocks and my old .fvwmrc file worked. All my old menu items were there and some even worked like xterms. ;)

BTW, calling Ubuntu *shoddy* here is like telling a mother that her baby is ugly.  Please realize even the ugliest baby is gorgeous to Mom. ;)

---

### Post by kerry_s on 2015-01-18
> **TheFu said:**
> I agree that a lighter GUI will make Ubuntu faster.  Most of the issue is with Unity, IMHO.  However, switching to a different distro just to have a different GUI seems excessive. GUIs are NOT the OS. In Linux, the GUI is just another program to be loaded, used or removed.  There must be 50 alternative GUIs and pretty much **any** of these will be faster than Unity without fail.

[Here are some of the most popular]("http://askubuntu.com/questions/65083/what-kinds-of-desktop-environments-and-shells-are-available") (with screenshots).

We are all a little different.  Back in 2010, I created a tiny customization for LXDE for my 80 yr old Mom to use that had the 5 things she wanted on the left side of the screen ... like the Unity appearance, but not at all that heavy or slow. Plus it wasn't sending anything Mom searched for to external parties (like Amazon), so it was FAST.  I know this to be true - Mom had a P4 with 1G of RAM, but when her motherboard failed, we swapped in a Core i7 with 6G of RAM. She didn't notice - because the outside of the box didn't look any different and everything was exactly the same.  I prodded her to say it was fast and eventually, she agreed, but I think she was just being nice.  LXDE is fast on most hardware still running today.  XFCE is also popular on lower-end hardware.

If these are too heavy, it is always possible to dump a DE completely and go old school with a pure WM (window manager) environment. Every DE is running a WM already, so these are well maintained, unless you do like me and try one from the mid-1990s out of nostalgia. BTW, fvwm still rocks and my old .fvwmrc file worked. All my old menu items were there and some even worked like xterms. ;)

BTW, calling Ubuntu *shoddy* here is like telling a mother that her baby is ugly.  Please realize even the ugliest baby is gorgeous to Mom. ;)

no, it's not just the gui, they tweak everything including the apps so it all works together better. in the next version the goal is all gtk3, but thats still work in progress.

---

### Post by TheFu on 2015-01-18
> **kerry_s said:**
> no, it's not just the gui, they tweak everything including the apps so it all works together better. in the next version the goal is all gtk3, but thats still work in progress.

I'm happily loading Ubuntu Server, then loading openbox and the 20 GUI programs I prefer on my desktops. Works fine for my needs. 

I think Canonical/Unity is aiming at a different group than me or the millions who run Mint or KDE, which is fine. 
I like that Canonical has the freedom to try things and take risks. Hopefully they will create a big hit. ;)

---

### Post by kerry_s on 2015-01-18
> **TheFu said:**
> I'm happily loading Ubuntu Server, then loading openbox and the 20 GUI programs I prefer on my desktops. Works fine for my needs. 

I think Canonical/Unity is aiming at a different group than me or the millions who run Mint or KDE, which is fine. 
I like that Canonical has the freedom to try things and take risks. Hopefully they will create a big hit. ;)

i agree, been distro hopping for about a week & half now trying all kinds of things. i keep coming back to debian gnome for my main os. it just feels so much faster than ubuntu to me, the desktop doesn't have that sluggish feel, startup is a little slow, but i use suspend & never turn off, so that don't matter to me. i might go back to elementary os if i want a ubuntu base, i like how it only has the base apps & you add what you want. it's like a custom install with out the hard work, its built on top of ubuntu 12 lts. for now i'm still learning gnome 3.

---

### Post by ajgreeny on 2015-01-18
Surprisingly, nobody so far has asked what hardware you are using 12.04 on, and this may be your problem.

Tell us what you have, in particular the graphic card and amount of ram.

My previous machine was a Sempron 2400+ with an old ATI 9200SE graphic card and 2GB ram.  I could not run Unity on that in any usable way; it would run but was *sooooo slooooow* as to be completely useless, perhaps mainly because of the graphic card. However, XFCE as the DE in Xubuntu ran very well with no major hold-ups or waiting for applications to start.

---

