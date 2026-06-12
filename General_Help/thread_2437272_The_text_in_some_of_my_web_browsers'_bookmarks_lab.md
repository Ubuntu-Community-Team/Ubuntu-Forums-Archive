---
title: "The text in some of my web browsers' bookmarks labels appears garbled (See pictures)"
date: 2020-02-20
forum: General Help
---

### Post by adel8 on 2020-02-20
Software:

- Ubuntu 18.04 LTS
- Chrome [COLOR=#5F6368][FONT=Roboto]version 79.0.3945.13
- Firefox 73.0
[/FONT][/COLOR]
How it appears:
[ATTACH=CONFIG]285062[/ATTACH][ATTACH=CONFIG]285063[/ATTACH][ATTACH=CONFIG]285064[/ATTACH]

This also occurs when hovering the cursor over other icons/buttons on the browser and webpage.
[ATTACH=CONFIG]285065[/ATTACH][ATTACH=CONFIG]285066[/ATTACH]

---

### Post by deadflowr on 2020-02-21
Chrome is old for one. Stable has reached version 80.XXX.
So you might want to update that.
Also, do you know the system specs like the gpu?
There was an issue with radeon graphics cards but has been fixed recently:
[https://bugs.launchpad.net/fedora/+source/xserver-xorg-video-ati/+bug/1841718]("https://bugs.launchpad.net/fedora/+source/xserver-xorg-video-ati/+bug/1841718")

If you cannot identify the specs some terminal commands to help are
```
uname -a 
inxi -F
lspci
lscpu
```
the first gives the current running kernel version in use.
the second will output most of the systems information
and the third and forth are just extras that will should basic devices and the cpu information.

(In some cases the inxi package is not installed (I believe the minimal desktop installation option doesn't come with it, or at least on one minimal install for me it wasn't) 
but lspci and lscpu definitely are, so if the inxi comes back not installed you can still quickly get the ls commands output, that can be helpful too,
which is why I added them; as a quick and easy fallback)

---

### Post by sdsurfer on 2020-02-21
I see this from time to time in FireFox. In my case, I lock screen, when I come back, the tabs do that garbled thing and I have to restart the browser, then all is fine. I always keep it updated to latest version.
It is a mild annoyance in my case and haven't dedicated time to finding the cause because it's sporadic. The closest I can guess is it is some issue with display drivers and FF. If pressed I would make sure video drivers are updated, and dig around in browser settings to see if there are any hardware or video settings that can be adjusted.

---

### Post by adel8 on 2020-02-21
Yeah. That Radeon/Xorg issue you mentioned is the same one I'm having. 

I read that thread, but I don't know how to downgrade xorg or install the new package.

Can you provide further guidance?

---

### Post by deadflowr on 2020-02-22
> I read that thread, but I don't know how to downgrade xorg or install the new package.
We don't know what you have, currently.
Look at
```
apt policy xserver-xorg-video-ati xserver-xorg-video-ati-hwe-18.04
```
post the results.

---

### Post by adel8 on 2020-02-23
[ATTACH=CONFIG]285077[/ATTACH]

---

