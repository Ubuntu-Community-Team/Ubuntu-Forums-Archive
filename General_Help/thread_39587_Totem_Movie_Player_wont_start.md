---
title: "Totem Movie Player wont start"
date: 2005-06-05
forum: General Help
---

### Post by henriette_holm on 2005-06-05
Hi.
I just did a fresh install of Ubuntu 5.04. When I try to start Totem from the Gnome Menu I get:

Totem could not startup
Resource busy or not available

Running it from the terminal doesn't make any difference (no error message there). Any suggestions?

-Henriette

---

### Post by royg1234 on 2005-06-05
try in terminal

```
sudo killall esd
```

if that fixes your problem, then see thread ["Howto: About sound in Hoary and Linux"](http://www.ubuntuforums.org/showthread.php?t=26567)

---

### Post by henriette_holm on 2005-06-06
That didn't fix it - same problem  :-|

---

### Post by royg1234 on 2005-06-07
Try this:

[http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly)

---

### Post by veritas366 on 2005-06-07
I got stuck one time with totem doing something weird.  probably not your issue, but  look in your applications>system tools>system monitor and see if totem is already playing.  I couldn't get totem to play once and I looked there and it was on like 7 times or something!  You can use kill all or use the gui to kill each instance.  I must have clicked on something more than once and then kept clicking on other files.  Each time totem was opening but was conflicting.  Probably not your problem, but worth a shot, given that error message.

---

### Post by henriette_holm on 2005-06-07
To veritas366: No, it wasn't that but thanks for the advise. I tried starting Totem while having the System Monitor running and the the process ends just after I click OK to the error message.

---

### Post by henriette_holm on 2005-06-07
Hi again.
I've followed both the guide ["How to configure sound to work properly in GNOME"](http://www.ubuntuguide.org/#configuresoundproperly) and ["Howto: about sound in Hoary & Linux"](http://http://www.ubuntuforums.org/showthread.php?t=26567) - basically two sides of the same story and everything BUT Totem is working just fine. It's not that I'm desparate for it to work. I'm just wondering how come it doesn't when it's included in the "basic" installation of Ubuntu. Is it just me having this problem?

-Henriette

---

### Post by simple on 2005-06-12
[QUOTE=henriette_holm]Hi again.
I've followed both the guide ["How to configure sound to work properly in GNOME"](http://www.ubuntuguide.org/#configuresoundproperly) and ["Howto: about sound in Hoary & Linux"](http://http://www.ubuntuforums.org/showthread.php?t=26567) - basically two sides of the same story and everything BUT Totem is working just fine. It's not that I'm desparate for it to work. I'm just wondering how come it doesn't when it's included in the "basic" installation of Ubuntu. Is it just me having this problem?

-Henriette[/QUOTE]
 i'm desperate for it to work. well i followed the first guide, the second guide links to microsoft.com? wtf is that.. i have an intel 915gv integrated chipset, so theres that and RealTek audio to choose from, then in gstreamer theres ESD ALSA and OSS so which should i use there? and i can't get mplayer now so i'm stuck.

---

### Post by mtb1 on 2005-06-15
From fedora forum.
Works for me
sWx

> I have the same problem, but if found out the by selecting
> 'XWindow (No Xv)', as default video sink, in the Multimedia System Selector then
> i can start Totem without any errors. But if i play some video in Totem, it dont
> look very good :-)))).
> If i select 'XWindows (X11/XShm/Xv)' and press the 'Test' buttom then i get an
> error "Faild to construct test pipeline for XWindows (X11/XShm/Xv)"

---

### Post by Xaruan on 2005-06-15
I've recently installed Ubuntu myself, and I got help on some of my noob questions.  I would suggest going to [www.ubuntuguide.org](www.ubuntuguide.org)  That site is great.

I downloaded most of the media players and codecs.  I can't speak for everyone but XINE worked the best for me.  Personally, I thought the totem player wasn't that great or didn't work as flawlessly as XINE did.

Hope this helps.

---

### Post by henriette_holm on 2005-06-15
> Hope this helps
Well, not really  ;-)  Don't get med wrong but I know of all the other media players which I'm happy enough to use instead. I just can't help but wonder how come Totem doesn't work on a new, clean install of Ubuntu 5.04.

-Henriette

---

### Post by jfunk on 2005-06-16
[QUOTE=mtb1]From fedora forum.
Works for me
sWx

> I have the same problem, but if found out the by selecting
> 'XWindow (No Xv)', as default video sink, in the Multimedia System Selector then
> i can start Totem without any errors. But if i play some video in Totem, it dont
> look very good :-)))).
> If i select 'XWindows (X11/XShm/Xv)' and press the 'Test' buttom then i get an
> error "Faild to construct test pipeline for XWindows (X11/XShm/Xv)"[/QUOTE]


This worked for me.  Most of the other options fail in both audio & video options, but the XWindow (No Xv) did pass test and player would open after that change.

Now I need to find codecs because it hasn't been able to play anything I've tried yet.  So far so good though.  I'm a total noob at this running it thru VMware on my XP machine and so far everythings been pretty easy.


j

---

