---
title: "Static / Feedback sound in headphones"
date: 2008-05-29
forum: General Help
---

### Post by atorch on 2008-05-29
Hi,

The title gives it away, mostly.

Some additional info:

- this started happening when I moved from Gutsy to Hardy, first via upgrade and then via fresh install

- the sound is always present when the headphones are plugged in and the sound volume is turned up, but it's only slightly audible when songs are playing

- in volume control...

 * muting the headphone OR master will make the sound stop

 * sliding the headphone or master volume down to nothing / zero percent, but without muting, will *not* make the sound stop

 * under the recording tab, moving the capture sliders up *adds* a new, much louder layer of static / watery sound to the one already there

- when un-muted, the computer speakers (volume control > front channel) do *not* produce this sound; it is only audible through the headphones

---

### Post by Zorael on 2008-05-29
Silly question, but: have you made sure that your mic output is muted? I've had the same problem and it took me a while to figure it out, heh. Fix it in [FONT="Courier New"]alsamixer[/FONT] entered in a terminal.

---

### Post by atorch on 2008-05-29
> **Zorael said:**
> Silly question, but: have you made sure that your mic output is muted? I've had the same problem and it took me a while to figure it out, heh. Fix it in [FONT="Courier New"]alsamixer[/FONT] entered in a terminal.

Does this look right?

---

### Post by Zorael on 2008-05-30
Hmm, I think so? MM means the channel is muted, which Front Mic seems to be.

What happens if you mute Off Hook? Headphone?

---

### Post by atorch on 2008-05-30
> **Zorael said:**
> Hmm, I think so? MM means the channel is muted, which Front Mic seems to be.

What happens if you mute Off Hook? Headphone?

mute Off Hook -> no change

mute headphone -> sound goes away

(* muting the headphone OR master will make the sound stop)

Important detail:
- when un-muted, the computer speakers (volume control > front channel) do *not* produce this sound; it is only audible through the headphones

...intuitively, that seems like it would limit the source / cause of this strange sound.

---

### Post by Zorael on 2008-05-30
Do you have a microphone to connect to your mic socket? If you do, does the sound it captures echo loudly in the speakers/headphones?

---

### Post by atorch on 2008-05-31
> **Zorael said:**
> Do you have a microphone to connect to your mic socket? If you do, does the sound it captures echo loudly in the speakers/headphones?

No, I don't have a mic.  I could try to find / borrow one... but in the meantime, can anything be tested without one?

---

### Post by Shinigami84 on 2008-11-25
I'm afraid this is the problem of headphones. I got this problem after purchasing Ultimate Ears Super.fi 5 Pro - it has low Impedance: 21 ohms, and that seems to be the cause. I have 3 other sets of headphones, all with impedance of 30 ohms or higher, and none have this problem.

Hope this helps. There seems to be no cure from this other than changing the headphones.

---

