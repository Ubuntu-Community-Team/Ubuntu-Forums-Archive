---
title: "Pulse keeps switching on and off in stroboscope speed"
date: 2021-11-04
forum: General Help
---

### Post by noob5000 on 2021-11-04
Pulse (on Ubuntu Studio 20.14) keeps disconnecting and connecting at flicker speed, without appearant cause (no hardware nor software environment changes aside from updates). Audio is unusable.

Where should I start? Under Windows I would reinstall lol. What alternatives are there on Ubuntu? Please halp...

---

### Post by noob5000 on 2021-11-04
Ok I rebooted with a live USB and the same problem appeared. It appears to be caused by the hardware :(

---

### Post by noob5000 on 2021-11-04
But when I reboot on the hdd installed 20.04 Ubuntu there are phases when Pulse seems stable for minutes, sometimes hours, then unstable again like mad.

Please, where should I start diagnosing?

---

### Post by dragonfly41 on 2021-11-05
Since this is a common issue across two different uses, then look for another common factor.

Bluetooth device perhaps? Just a theory.

[https://askubuntu.com/questions/475987/a2dp-on-pulseaudio-terrible-choppy-skipping-audio](https://askubuntu.com/questions/475987/a2dp-on-pulseaudio-terrible-choppy-skipping-audio)

---

### Post by noob5000 on 2021-11-05
^ Thanks for the guess. No bluetooth device is present in my machine though.

In today's attempt I booted up the machine and noticed that Pulse seems stable. However, no sound audible. I tried moving the audio cable pin in the onboard output connector and it turned out to be a loose contact. Sound works again, Pulse keeps acting normal. 

I wonder, could that have been it? Could the loose contact possibly have thrown Pulse off to the degree of disconnecting and connecting several times per second?

---

### Post by dragonfly41 on 2021-11-05
Sure. A loose connection could act like a morse code transmitter.
Many other such scenarios seen with electronic circuits.
Bad connection of RAM etc.

---

### Post by noob5000 on 2021-11-05
That makes sense, thank you for the explanation! 

And quite a relief, too. I was beginning to be afraid of the mainboard giving up the ghost or something even worse.

---

