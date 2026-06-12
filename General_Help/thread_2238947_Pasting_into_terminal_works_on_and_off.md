---
title: "Pasting into terminal works on and off"
date: 2014-08-11
forum: General Help
---

### Post by ffrr on 2014-08-11
Ubuntu 12.04LTS. After working flawlessly the terminal pasting functionality turned erratic at some point which I can't relate to any preceding occurrence. I spent a few hours scouring this forum and found relevant comments and suggestions, but nothing conclusive. I also mention, whether or not it matters, that quite some time before the problem started, I had gotten rid of malfunctions that seemed related to compiz (being no longer supported?). Following a related thread on this forum I downgraded with "apt-get install gnome-session-fallback". The downgrade may have introduced confusion with clipboards. 

Thanks for suggestions, including pointers to literature that explains the system components

ffrr

---

### Post by TheFu on 2014-08-11
For 30 yrs, the X-buffer was used. All was correct in the world.  Then a bunch of yunnin's decided that wasn't good enough and added other clipboards.  Other projects like Mozilla saw this and decided to mess the the X-buffer too. Then DEs became popular and started screwing with the X-buffer more.

For about the last 10 yrs, select/paste has only worked properly with real X/Windows applications.  I find the Mozilla apps to be the worst at screwing this up.

I can only offer condolences and suggest that removing as many "clipboard" manager as possible to simplify the environment. Different programs will use different select/paste methods too - notice I'm NOT saying "copy" ... that isn't the native X/Windows method.

If you need/want a more complicated copy buffer program - add only 1 of them based on the environment you use most and know that programs built with other libraries may not support it.  In theory, the X-buffer should work with all X/Windows programs of any level, but I've found a few Gnome programs that seem to ignore it completely.  Whoever wrote those programs - well - THEY SUCK!

I hope this makes sense.  BTW, I was an X/Windows programmer for about a decade.  Not using the X-buffer means that the programmer had to code something special - it sorta just works by default.

---

### Post by ffrr on 2014-08-13
TheFu

Thank you for your comments. I gather that there is a lack of coordination in terms of clipboard management. I'd like to downgrade to the state I was in a couple of years ago, when everything worked right. But I neither know what that state exactly was, nor how I would restore it if I knew. In addition I'd prefer to upgrade, hoping that the good people who do the heavy lifiting will eventually fix the problem. I just received a notice recommending version 14 point something. Might that help? I don't jump on every upgrade, especially since the LTS attribute I now have somehow suggests a lower degree of volatility than a newer version without LTS. 

Perhaps one or the other might have found a fix that worked for h(er|im) and would be so kind to share it.

Thanks

ffrr

---

### Post by TheFu on 2014-08-13
So you are on 12.04?  If you are happy, stay there a few more months ... or as long as you like until 2017. 
I have a number of servers on 12.04 and don't plan to change until 2016-ish.

As to my desktops - most are on 14.04 now, also an LTS.  Some things are better, some things are worse. It will becomes more stable after 14.10 is released, because all the "cool kids" will migrate to that release. You and I know that computers are for getting things done, not just to upgrade constantly and patch. ;)

I will admit that my C720 chromebook is so new that only 14.04 had the hardware support I needed to make the experience reasonably good. 13.10 sucked and anything prior wouldn't work with the touchpad.

I haven't seen any changes related to clipboards since DEs became popular and doubt that will ever happen as long as we/you run a DE. By using a pure-WM environment, you can gain more control, especially over the x-buffer - forget clipboards. I just want the x-buffer to work as it is designed without being molested.  I don't need multi-level buffers with my select/paste.

For the reasoning behind why it is the way it is ... read **The Cathedral and the Bazaar**. It is just a trade-off for the way that our OS and applications are created. ;)  All in all, I'm much happier with this method than having a dictator.

---

### Post by ffrr on 2014-08-16
TheFu
   Forgive the delay. I've been on to other things. Thanks for your comments. Also forgive my moderate tech wizzardy. I don't exactly know what my DE is. Is it some version of GNOME? There is a bash command that displays the whole machine. I found it one day reading thread, tried it out and made a note of it, but didn't note where I made the not, so . . . 
   I don't need multi-level buffers either. How would I get rid of them. How from here to a pure WM environment? 
ffrr

---

### Post by grahammechanical on 2014-08-16
> [COLOR=#000000]compiz (being no longer supported?).[/COLOR]

Compiz the window compositor/manager is in Ubuntu 14.04 and that will be supported until April 2019. It is also in the next release of Ubuntu - 14.10. And will likely be in 15.04 but by 16.04 Compiz along with LightDM and the Xserver will be replaced by Mir. So there is continued support for Compiz years to come.

Perhaps you are thinking of Compiz Configuration Settings Manager (CCSM)? The main developer decided not to work on CCSM and for a time it seemed that CCSM would not be supported any more but 2 different developers took up the task.

Regards.

---

### Post by TheFu on 2014-08-17
> **ffrr said:**
> TheFu
   Forgive the delay. I've been on to other things. Thanks for your comments. Also forgive my moderate tech wizzardy. I don't exactly know what my DE is. Is it some version of GNOME? There is a bash command that displays the whole machine. I found it one day reading thread, tried it out and made a note of it, but didn't note where I made the not, so . . . 
   I don't need multi-level buffers either. How would I get rid of them. How from here to a pure WM environment? 
ffrr

DE - [Desktop Environment]("https://en.wikipedia.org/wiki/Desktop_environment") - it is usually seen by having a panel of icons/options/menu. Unity, Gnome, KDE, XFCE, LXDE are examples. There are probably 20+ others.

WM - [Window Manager]("https://en.wikipedia.org/wiki/Window_manager") - this is the software that controls were a GUI application is placed, the thickness of the border around each, the title and the thing that lets us "grab" and move a window.  WMs also have menus, usually accessed by right-clicking on a blank part of the desktop. openbox, fluxbox, fvwm, twm, wmw, and about 50 others exist. The link has a nice picture, though things appear to have changed since I was an X/Windows programmer in the mid-90s.

A WM can run alone, I often use just openbox without any DE.  A DE requires a WM to work.

---

### Post by ffrr on 2014-08-19
Thank you both for the tips. I'll have to digest them. I think I'll find a thorough explanation of the desktop, its components, options and how they stack and interact. When I switched from Windows to Ubuntu--must be three or four years ago--everything worked fine straight out of the box. Perhaps upgrading to 14.10 might get me another snagfree configuration. As I said earlier, I don't want to upgrade twice a year. But currently I would be happy with a version whose components don't fight with each other.

ffrr

---

### Post by TheFu on 2014-08-19
Be certain you understand the difference between an LTS and non-LTS release.  I would strongly suggest you NOT touch any NON-LTS releases if you want a stable system. Try different DEs, different WM - sure, but stay on LTS.
[http://blog.jdpfu.com/2013/07/19/why-ubuntu-users-should-run-an-lts-release](http://blog.jdpfu.com/2013/07/19/why-ubuntu-users-should-run-an-lts-release)

I've said my piece. Good luck, regardless of what you decide.

---

### Post by ffrr on 2014-08-23
Thanks . . .

---

