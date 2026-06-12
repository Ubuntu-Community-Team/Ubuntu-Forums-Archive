---
title: "weird problem with evolution/exchange/wm5 syncing..."
date: 2007-05-14
forum: General Help
---

### Post by zombiepig on 2007-05-14
Using Ubuntu 7.04, i've setup evolution to connect to an exchange backend (running exchange 2003 on a sbs). This works fine (most of the time :P), and changes i make in the calender in evolution are reflected when i check via owa. 

HOWEVER (this is where the weirdness kicks in!), i'm also syncing a wm5 phone to the exchange server using wifi. this works fine for everything EXCEPT appointments made in evolution, which fail to appear at all. 
In other words - I make an appointment in evolution, it syncs to the exchange server and viewing the appointment works via owa, but if i then sync my phone the appointment never reaches the phone. If i open the appointment in owa, make a small change, then try re-syncing my phone it then syncs the appointment correctly :S

So it seems to me that something in the appointments created by the evolution exchange backend is slightly different to normal appointments stored on the exchange server... thus preventing the wm5 sync. Is this a known bug, something I'm doing wrong, or misconfiguration? 

(I'm relatively new with Linux/Ubuntu and am enjoying learning all these new technologies... but my linux troubleshooting skills are almost non-existant :P)

---

### Post by dazzpj on 2007-05-17
I see the same problem (amongst others) and have discovered that if you set the appointment to be private in evolution it will sync and show up on the WM device, of course this is less than desirable if you are receiving appointments sent from other Outlook users as they are all public by default, still it is something.

---

### Post by zombiepig on 2007-05-17
ok just tested that and it works - good enough for me :P

is there a way to make this the default for new items?

---

### Post by dazzpj on 2007-05-18
not that I have found no, this is half the problem, if you are connected to a corporate exchange server as I am and receive meeting requests from others, they are all set to public by default (as they should be) and so they dont show up when i sync my WM device, anoying realy but the alternative is returning to Windows and Outlook and that doesnt even bear thought....

---

### Post by ThomasNovin on 2007-10-22
There is a bug about this on [http://bugzilla.gnome.org/show_bug.cgi?id=403903](http://bugzilla.gnome.org/show_bug.cgi?id=403903). The bug has gotten no attention though. If you have this problem, please let the developers know it!

---

