---
title: "No sound in Gaim"
date: 2005-07-24
forum: General Help
---

### Post by web250 on 2005-07-24
I'm having trouble getting sound in Gaim to work. It sometimes works using arts, but once I open say XMMS, and use ALSA for my sound, the sound in gaim stops working. I've tried setting it to automatic and editing the libao file to say default_driver=alsa but that doesnt work. 

I'm using gaim 1.4.0 via a backport, and my sound is nforce2.

---

### Post by varunus on 2005-07-24
Sounds like you need to follow this howto:
[http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063)

I personally recommend using:
```

period_size 1024
buffer_size 4096 # increase to 8192 if you have scratchy problems	
```

These settings get rid of the sound lag a lot of ppl complain about after following that howto.

Once you do this, all programs should be able to play sounds at once.  Make sure to set arts to use ALSA or ESD for output.

---

### Post by web250 on 2005-07-24
I actually ended up using the nforce2 how-to from this site. It works great, i have sound in botch XMMS and GAIM at the same time.

MY only problem is that XMMS randomly pauses every once in a while, no explanation to why

---

