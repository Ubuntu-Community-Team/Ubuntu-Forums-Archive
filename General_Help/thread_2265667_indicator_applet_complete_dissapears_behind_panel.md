---
title: "indicator applet complete dissapears behind panel"
date: 2015-02-16
forum: General Help
---

### Post by lauricat on 2015-02-16
G'day.

I have an annoying proiblem on both of my Ubuntu machines; one a Laptop running 12.04 and classic theme login. The other my desktop running 14.04 - ambiance theme that I login in with Classic as well. It is with the indicator applet complete that I use with both. Note both have the one panel at the bottom of the screen

The problem is when I need to disconnect, reconnect, muliple networks, edit them, etc it can cause the pop up to expand up, which is what it's supposed to do. But sometimes after I play around with the nework settings, it collapses again like it should, the next time I try and use it (ie select a different wireless network to test, or access 'edit network connections' ) it causes the pop up to NOT expand up and stay hidden. 

There is a little arrow I can usually expand further up if I can't see all the available options on the Networking part of the applet - when it works correctly, but when it's playing up (ie. stays totally behind the panel, and not expand up) the little arrow is not there either.

This is very annoying if I need to sort out networking on a job - I loose the ability to quickly change network configs -  the only solution is reboot. It only happens with the networking part of the applet. The problem only happens after I utilise the network part of the applet constantly.

Could it be that the applet is designed to work with the panel on the top of the screen - not bottom  as I have it configured.

I can attach a screen shot, but you can't really see what is happening as as I say the part of applet I need to use disapears. 

Cheers & Thanks

~L.

---

### Post by kerry_s on 2015-02-16
i don't think you need to restart. just restarting the panel should be good enough or loging out & back in.

if i had that kind of issue i'd most likely put a script or launcher on the desktop with something like:

killall gnome-panel && gnome-panel &

is it gnome-panel in classic ? lol

---

### Post by lauricat on 2015-02-16
Yes it is. Just thought someone else may have had this problem. Frustrating as I use the Network bit of the applet the most.

---

