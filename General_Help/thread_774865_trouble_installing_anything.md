---
title: "trouble installing anything"
date: 2008-04-29
forum: General Help
---

### Post by JoeStoppable on 2008-04-29
I dont know what happened, but I tried installing limewire and it was freezing up so i just shut my comp down. and now i was in the add/remove program trying to put in this video codec the Gstreamer Dirac video plugin after i press apply changes it gives me this message 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

It also says that for every other thing i try to do. Please help

Oh umm p.s. this is my first time using linux or ubuntu or whatever. but i use ubuntu

---

### Post by scragar on 2008-04-29
just open a terminal (Application > accessories > Terminal ) and copy/paste in this:
```
sudo dpkg --configure -a
```

when it's done you should be able to install things again.

---

### Post by JoeStoppable on 2008-04-29
thanks that fixed it really well. I guess if its not too much trouble, i'm trying to find out whats wrong but some of the anime that i'm watching has some like wierd video like pixelation and i guess kinda lag.

I'm positive its the codec cause it used to work fine on my windows. I had a lot of different codec's but they dont work for linux. So any idea's? The only codecs i have are the ones that came default with ubuntu

---

### Post by scragar on 2008-04-29
Try installing VLC media player, it saves having to search around for the codecs manualy since they are all built into it.  I've never worked out what codecs are required for what files, so the fact that VLC doesn't need them has always been a big plus for me.

---

