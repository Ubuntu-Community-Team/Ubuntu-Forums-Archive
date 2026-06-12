---
title: "DVD ripping"
date: 2014-08-06
forum: General Help
---

### Post by UncleMonty on 2014-08-06
As of 14.04 - what is the best way of ripping dvds, please?

---

### Post by SuperFreak on 2014-08-06
K3b

---

### Post by ibjsb4 on 2014-08-06
K3b is solid, an excellent performer, but it pulls in a lot of kde packets.

I switched to xfburn which works well, just not as many dependencies or bells and whistles.

---

### Post by Imperium Guard on 2014-08-15
I used the command "dd" to rip a DVD to an .iso file, with /dev/sr0 being my DVD drive (may vary with other computers). ```
dd if=/dev/sr0 of=filename.iso
```

**Be careful with the command dd, as it can overwrite and destroy data.**

---

### Post by Rob Sayer on 2014-08-16
Actually the above methods will work with some dvd's but not with newer copy protection schemes.  This is the facts of life with open source ... proprietary standards are either slowly dealt with or not at all.

What I'd do if I had no Windows partition is run DVDFab Free HD DEcrypter (the free part of dvdfab) using Wine, in which it apparently works fine according to the wine docs.

When I say 'rip' I mean to just copy the disc contents to a VIDEO_TS folder.  That is actually what 'rip' means, but many media noobs think it means rip *and* reencode/compress, which is a separate process that some rippers combine.

You'd be better off using handbrake or avidemux to re encode the video_ts files to something smaller if that's what you want.  I've never seen a combined ripper/encoder whose encoder didn't stink, dvdfab included.

---

