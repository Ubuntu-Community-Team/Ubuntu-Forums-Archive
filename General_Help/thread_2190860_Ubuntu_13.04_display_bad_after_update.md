---
title: "Ubuntu 13.04 display bad after update"
date: 2013-11-29
forum: General Help
---

### Post by jbuczek on 2013-11-29
I just got internet service back after an interruption of almost two months. (A major earthquake and two major typhoons including the biggest one in history.  Yes, I'm in the Philippines.) 

Ubuntu Updater immediately told me that there were 228 updates pending.  I told it to go right ahead.  After a couple hours it said it was done and requested a reboot.  After the boot the display was significently screwed up.

> after being closed, windows don't disappear.  They shrink a bit and blur.  This includes the dash and the launcher when on autohide.
> dragging a window leaves copies of it behind every few pixels.
> fonts for desktop icons are VERY bright and seem to be double printed with a slight displacement.

The trash left behind can be cleared by going to the Workspace Switcher briefly and returning.  When you do this the first time the wallpaper disappears, along with the trash, and from then on the desktop is black.  The smear from the launcher when on autohide does not clean up.

Everything inside an active window is normal.

I tried cold boot and a different login.  

I rebooted and backed up to older kernal versions.

I tried apt-get autoclean, purge, etc. in case there were remnants of some update left around causing trouble.

Nothing changed.

I have a fairly vanilla Ubuntu 13.04 with Unity.

Hardware is a Gigabyte 880GM-DH2 mb with Athlon II X2 240 and 4 GB of DDR3/1333.  It's all been working fine for six months.

Display is on board.  I don't remember what it is and a quick Google didn't tell me.  ATI something I'm pretty sure.  "Software and Updates" tells me I'm NOT using any propriatary drivers.

I could use some help.  After being internet starved for two months I've got a lot of catching up to do.  Please don't tell me I need a clean install.  Last time it was weeks before I got everything right again.

TIA

---

### Post by stinkeye on 2013-11-29
Try resetting unity/compiz....
```
dconf reset -f /org/compiz/
```
Log out then back in.

To get a session you can work in while trying to fix, install gnome fallback.
All that's needed is...
```
sudo apt-get install gnome-panel
```

Then at the login screen choose the **Gnome Fallback(no effects)** session.
You want the '(no effects)" session because it doesn't use compiz.

Also what's the output from  ...
```
/usr/lib/nux/unity_support_test -p
```

---

### Post by jbuczek on 2013-11-29
result of dconf reset -f /org/compiz/

        Screen is much worse, broken up into small squares containing randomized segments of the original desktop image.
        Workspace Switcher has disappeared so I can no longer clean things up.

Result of /usr/lib/nux/unity_support_test -p

OpenGL vendor string:   X.Org
OpenGL renderer string: Gallium 0.4 on AMD RS880
OpenGL version string:  3.0 Mesa 9.1.7

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

I wanted to get this out in case the "sudo apt-get install gnome-panel" option left me with nothing.

I will now sign off and try that.

---

### Post by Mark Phelps on 2013-11-29
> Display is on board. I don't remember what it is and a quick Google didn't tell me. ATI something I'm pretty sure. 

Quick Google told me that your motherboard has an HD 4250 chipset on it.

With anything newer than Ubuntu 12.04.1, you need to be using the open-source Radeon drivers -- which should work OK for you. If you were using them earlier in 13.04, they should still be working OK.

---

### Post by jbuczek on 2013-11-29
TO "stinkeye"

OK - "sudo apt-get install gnome-panel" gave me "gnome-panel is already the latest version".

I log out and the display options are: Cinnamon, Cinnamon (software), Ubuntu (default)

No option for " Gnome Fallback(no effects)" but I assume that is of no consequence to this issue.

Cinnamon works fine.  I had forgotten that i played with it for a while way back when.  

So now I have a working session.   How do I fix Unity?

TO: Mark Phelps

Never had the Radeon open source drivers installed and Software and Updates Additional Drivers section does not offer them to me.

I'm seriously thinking about going to something like LMDE (Linux Mint Debian Edition) and let Shuttleworth and Ming the Merciless conquer the universe without me.  Unfortunately I don't have time right now. <G>.

---

### Post by jbuczek on 2013-11-29
Just to be clear.

I've been using 13.04 since a month after it came out..... I hate being a pioneer.  Everything always worked fine.  This problem happened after an UPDATE not an UPGRADE... in case I left any confusion about that.

---

### Post by jbuczek on 2013-12-07
OK.... it's been a week and no more suggestions and nothing I can find by my own research suggests how to repair Unity..... and...... Cinnamon is working fine.  Better than fine because today I decided to completely remove Unity and stick with Cinnamon and now displays are snappier, graphics are crisper and large applications start and stop noticably faster.  I added Cairo-dock and I feel I now have 99% of what I liked about Unity and zero of what I didn't like.  Next LTS release of Linux Mint I guess I'll switch over completely with a clean install.

Thanx to those to tried to help.

---

