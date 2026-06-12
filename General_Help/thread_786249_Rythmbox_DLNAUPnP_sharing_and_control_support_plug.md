---
title: "Rythmbox DLNA/UPnP sharing and control support plugin Help!"
date: 2008-05-08
forum: General Help
---

### Post by illbashu on 2008-05-08
how do i install the DLNA/UPnP sharing and control support plugin ? every time i open rhythmbox i get an error saying "Unable to activate plugin DLNA/UPnP sharing and control support"

---

### Post by illbashu on 2008-05-08
[IMG]http://tbn0.google.com/images?q=tbn:TH21BagGi-HbnM:http://bp2.blogger.com/_scZrDxRlDo8/RqlSB9mwuAI/AAAAAAAAAAs/21rLrYkanZo/s320/bumpage.jpg[/IMG]!

---

### Post by Mirzabah on 2008-05-09
There's a [debian bug report]("http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/ec1ef5cee57ccfd5") for this. Long story short, open up a terminal and execute the following command:

```
sudo apt-get install python-coherence
```

Or install the python-coherence package using Synaptic. Either way, it works a treat :)

---

### Post by illbashu on 2008-05-09
so, does this work with the 360?

---

### Post by darthpenguin on 2009-04-13
I did this and all seems well in rythymbox but my ps3 will see rythymbox and the tacks but will not play the tracks. just a visualization (the earth one) but no sound or track information. any ideas? thx

---

### Post by x C0MMAND0 x on 2009-05-08
Or any idea getting this to work with Xbox 360?

---

### Post by benste on 2009-07-30
I'm interested in this topic to and trying out some things with Win 7 WMP (in a VM) and Rhytmbox(coherence plugin)

The device is detected as play on, but service is not available, I'll keep on searching and update this thread or a bug report if I've got something new.
looking at
[http://coherence.beebits.net/wiki/RhythmBox]("http://coherence.beebits.net/wiki/RhythmBox")
it's menitioned that Ubuntu shippes a too old version, so I'll give it a try with karmic and some self build packages.

---

### Post by destructaball on 2009-12-20
The PS3 problem is one that I used to have, it wasn't that it wasn't playing, it just took agers to buffer. A new router sorted out the problem for one reason or another wireless B just didn't cut it but I feel there is another way round this

---

### Post by dually on 2011-02-21
So I ran this command through a terminal,  (sudo apt-get install python-coherence)  but I'm not seeing "DLNA/UPnP" in the list of plugins in rhythm box.  Is it called something else now?

---

### Post by dually on 2011-02-25
So I was able to get rhythm box to manifest the dlna plugin option by brute force installing everything in the synaptics menu that seemed related.  My ps3 and logitech revue both now "see" rhythmbox and mediatomb.  However, neither device seems to be able to rationalize any of the actual tracks, only the folders artists and albums via rhythmbox (but not even that for media tomb).  The rhythmbox on the pc will actually manifest and play the 5000 or so tracks that I have on a usb hard drive.  Ubuntu 10.10 installed with wubi "alongside" windows xp.

---

