---
title: "Things to make your system faster?"
date: 2008-05-20
forum: General Help
---

### Post by Tom--d on 2008-05-20
How can I tweak my system so that its faster?


I'm on Ubuntu 8.04.

---

### Post by atomkarinca on 2008-05-20
You can try using other lightweight file managers like Thunar or PCManFM; you can try disabling startup programs you don't use; you can try using lightweight alternatives of the applications you use.

---

### Post by Tom--d on 2008-05-20
I have disabled/deleted all of the unwanted start up programs.

Anything in general. Something which will effect the whole system?

Just would like my pc faster than it is now :p

---

### Post by amingv on 2008-05-20
K.Mandla maintains a how-to to set up many versions of Ubuntu for speed, you might like to check it out:

[http://kmandla.wordpress.com/2008/05/04/howto-set-up-hardy-for-speed/](http://kmandla.wordpress.com/2008/05/04/howto-set-up-hardy-for-speed/)

---

### Post by kerry_s on 2008-05-20
what is your system?

i build mine from a base up so it's quick right out of the box, i use light programs and window manager.

first thing would be trim any services that aren't really needed, only you can decide what you need.

the bulk of my time is spent in the browser, so at the top of my list is a host block file->
[http://www.mvps.org/winhelp2002/hosts.txt](http://www.mvps.org/winhelp2002/hosts.txt)

sudo -i
cat hosts.txt >> /etc/hosts

blocks most of the bad.

i usually disable pango using /etc/environment
MOZ_DISABLE_PANGO=1

the common firefox pipeling tweaks.

i fine tune my vid driver in xorg.conf for neomagic.

that's about it for me.

---

### Post by Tom--d on 2008-05-20
I have a fast laptop. 

Just want some fine tuning to be done :D

Services... I do not really know whats what really. What should I be disabling?

---

### Post by kerry_s on 2008-05-20
> **Tom--d said:**
> I have a fast laptop. 

Just want some fine tuning to be done :D

Services... I do not really know whats what really. What should I be disabling?


forget fine tunning then, first dump that heavy de, use a light window manager, try not to use anything tied to gnome that requires gnome crap to run. rule of thumb, the bigger the program, the slower it will be.
examples:
if you only need to view a doc use abiword instead of openoffice.
pdf, epdfview instead of evince
filemanager, rox is one of the quickest around, but lacks in looks stock, it can of course be changed. there's many to choose from, but for top speed command line never fails, i like a little luxury so i use a command line file manager "clex", but there also "mc" most common used, lots of features built in, takes a bit of learning.

speed requires thinking outside the box, first realize whats actually making it fell slow, then working from there. like for instance, is it slow to respond when you click, maybe the way it draws on the screen, does it do it every time or just the first time, etc...

---

### Post by Tom--d on 2008-05-21
I can see where you are going.

Nothing is making it slow that I know off. 

I was just wondering if I could make it just a little bit faster ^_^

Services.. I don't know where to start. I know bluetooth and dont need that. Is there a hotto with them? That would really help :)

Like make the system, Overall, a bit faster. Faster loading apps etc? Faster start up. 
Even tho it takes 50secs to start up (from what Conky says)
O yes, I use Gnome.. but I like it :) 
I like compiz :D
I know its quite a 'heavy' WM but I can live with that. I have used xfce and kde. xfce is really nice :) 
Just got to make it look really good :D 
And can you have compiz running with xfce?

File management could do with a change. Nautilus is a bit heavy in cases. I will look at rox. 


Thanks.
Tom :)

---

### Post by Coplen on 2008-05-21
> **Tom--d said:**
> 
And can you have compiz running with xfce?

Thanks.
Tom :)

Yes. alt-f2 and then enter compiz --replace

Also under Applications>Settings>Settings Manager>Autostarted apss add this line:

compiz --replace

That will autostart compiz when xfce loads. The screen will flicker briefly each time you load xfce, but that's minor.

---

