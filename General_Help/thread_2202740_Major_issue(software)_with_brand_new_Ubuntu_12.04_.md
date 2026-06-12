---
title: "Major issue(software?) with brand new Ubuntu 12.04 installation."
date: 2014-01-30
forum: General Help
---

### Post by SteveL1990 on 2014-01-30
Hey fellas. 

Recently, I installed 12.04(Precise) as a secondary OS on one of my laptops(a
Toshiba Satellite), after over a year of using Natty on the other PC, and was
able to install the new system without any issues. And because I figured I'd
be keeping this computer for a little while, I thought I'd go ahead and download
a few new programs to go along with it.

They are, in no particular order:

KolourPaint
VLC Media Player
BurgerSpace
O A.D.
XMille
FreeCiv
Links
Htop
Midnight Commander
VirtualBox
Kate
GParted
and Opera.

And for the first couple of days, everything ran quite smoothly, no issues or anything. Unfortunately, 
however, that didn't last. Late last night I came back to my computer after a short absence and noticed
that the screen was just totally pitch black, like as if it were about to go into sleep mode or something
(though my PC's battery light wasn't flashing, which it does do every time the PC is about to run out of
juice). I tried moving the mouse around for a little bit, about 10 seconds to be more precise, but to no
avail. 

I began to think that something might possibly have gone quite wrong(a similar incident occurred a couple of 
years ago with my other computer when I was still primarily a Windows user), so I decided to go into Recovery Mode. 
Immediately I thought of the possibility of broken packages, so I went
to the "Fix Broken Packages" option. That, unfortunately, went nowhere; all of the links were broken, with no 
hope of retrieval(I tried a couple of the suggested apt-get options, neither of which did jack squat, either).
I then tried the "Delete Unused Packages" option; I cleared up a tiny bit of disk space but given that most, if
not all of the stuff that was erased appeared to be Firefox related, I realized that it probably wouldn't have 
done any good. I then just gave up and did a disk check then rebooted again, this time to Ubuntu. Unfortunately,
it seems that the trouble was only just beginning; I'll try to do my best to explain the problems 
as I discovered them, and there were, unfortunately, quite a few to be found.

I hadn't noticed anything particularly off at first. It was when I tried to play XMille that I realized there 
was an issue. The game.....simply would not work. At all. And when I attempted to close it, the darn thing
wouldn't respond. At all. Clicking the X button got me no results at all; the button wouldn't even highlight,
as if the cursor was nowhere near it!

I hoped that this was merely just an issue with the individual program, but the same thing happened with 
FreeCiv, too. 

But perhaps the most distressing problems developed when I tried to use Opera; it was just acting 
*rather* ornery in general; X buttons not responding, can't push play or pause on a YouTube video, etc.
And even the mouse functions seemed to be broken; there were times where I had to try to fumble with
the *keyboard* to get anything done or wait for the program to unscrew itself. 

And it's not just Opera. A few other programs have had those same issues as well; won't recognize the
mouse cursor(i.e. X button doesn't light up when cursor moves over it), clicking doesn't work, 
having to screw around with the keyboard to save, exit, etc.

There's even been issues with the menu, in which clicking on icons does absolutely nothing, even 
if it was fine just a minute ago. In fact, this issue, too, has been a problem in general. 
One moment, Kate, or Opera, etc., might be working just fine and the next moment it's acting
all wonky(as described above). And there's even been times where just about the whole thing will
freeze up except for the cursor, and nothing else.

 And none of this was a problem before last night. 

I dunno what to do now, TBH. I don't want to have
to go thru the trouble of reinstalling my system so soon unless I have no other options, so I 
really truly do need the help here. :(

---

### Post by EnglishElectricAndy on 2014-01-31
Hi, please could you post your hardware specs i.e:

Type of CPU and GHz clock speed
Amount of RAM installed
Graphics driver

Full-fat high-caffeine 12.04 prefers plenty of headroom to operate effectively. A lot of the symptoms you describe point towards the system using swap, which in turn indicates it's running out of headroom in RAM.

---

### Post by Impavidus on 2014-01-31
Sounds a bit like a problem I had just an hour ago. I couldn't type in firefox, only scrolling with the scrollwheel in firefox worked, no mouse buttons and the workspace switcher didn't work either. It was definitely not swapping. Switching to a console and killing xfce-session worked. There may be a less drastic solution. It sounds like a problem with the window manager or something related.

---

### Post by Bucky Ball on 2014-01-31
Did this happen after an update or upgrade? Could you open a terminal and run:

```
sudo apt-get update
```

If no errors, run:
```

sudo apt-get upgrade
```

Report any and all errors exactly as they appear. Thanks.

Also, try killing the xsession, as suggested by Impavidus.

---

### Post by SteveL1990 on 2014-01-31
> **EnglishElectricAndy said:**
> Hi, please could you post your hardware specs i.e:

Type of CPU and GHz clock speed
Amount of RAM installed
Graphics driver

Full-fat high-caffeine 12.04 prefers plenty of headroom to operate effectively. A lot of the symptoms you describe point towards the system using swap, which in turn indicates it's running out of headroom in RAM.

I've got 4 GB of RAM, and about 2.20 GHz worth of clock speed with 2 CPUs. 

> **Impavidus said:**
> Sounds a bit like a problem I had just an hour ago. I couldn't type in firefox, only scrolling with the scrollwheel in firefox worked, no mouse buttons and the workspace switcher didn't work either. It was definitely not swapping. Switching to a console and killing xfce-session worked. There may be a less drastic solution. It sounds like a problem with the window manager or something related.

> **Bucky Ball said:**
> Did this happen after an update or upgrade? Could you open a terminal and run:

```
sudo apt-get update
```

If no errors, run:
```

sudo apt-get upgrade
```

Report any and all errors exactly as they appear. Thanks.

Also, try killing the xsession, as suggested by Impavidus.

Unfortunately, there's been times where I've been unable to do anything at all in the GUI mode(not even open a terminal), other than the program or browser that I was currently using, once the problems started. (in fact, this was happening right as I was typing this response.). 

I was, at least, able to exit to console mode, but I had trouble figuring out how to stop the xfce-session, though. 

Also, when I installed Ubuntu initially, I actually decided to install updates with it, and didn't try to install any more after that.

Edit: I was able to run both sudo functions in a Terminal, and it reported no errors.

---

