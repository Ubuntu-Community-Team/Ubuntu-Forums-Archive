---
title: "wrong alsa module installed. i need emu10k1"
date: 2007-12-05
forum: General Help
---

### Post by ryan461 on 2007-12-05
im using a creative sound blaster live card. it works perfect with my 5.1 speakers on windows. on ubuntu it is using the CA0106 module which is crap. It can only use analog audio. I want emu10k1 to get pcm control. Now i entered lspci in a terminal and it said that i have 
02:09.0 Multimedia audio controller: Creative Labs SB Audigy LS

which isnt correct.

any ideas? tutorials?

---

### Post by bodhi.zazen on 2007-12-05
```
sudo modprobe snd-emu10k1
```

If that works, edit /etc/modules and add in snd-emu10k1

---

### Post by kerry_s on 2007-12-05
you can also try " **sudo alsaconf** " to set up alsa.

---

### Post by ryan461 on 2007-12-05
> **bodhi.zazen said:**
> ```
sudo modprobe snd-emu10k1
```

If that works, edit /etc/modules and add in snd-emu10k1

how can i check that it did work? i ran the command, and just went to the next line. real quick for an install

---

### Post by bodhi.zazen on 2007-12-05
It does not install anything, just loads a kernel module, or the driver for your sound card.

How is your system sound ?

---

### Post by ryan461 on 2007-12-05
well after loading, it placed me onto an an HDA Nvidia controller. would work if i was plugged into the motherboard. but that is not the case.

I have not checked the system sound, how can i go about doing that?

---

### Post by ryan461 on 2007-12-05
bump

---

### Post by ikester8 on 2008-05-04
I had the same problem. I found a solution to mine here:

[https://bugs.launchpad.net/ubuntu/+bug/179095/comments/21](https://bugs.launchpad.net/ubuntu/+bug/179095/comments/21)

Try this from terminal:

sudo alsamixer

Look for Audigy Analog/Digital Output Jack. Type "m" to mute. Esc to exit.

Then try playing something.

---

