---
title: "No sound"
date: 2007-09-09
forum: General Help
---

### Post by goldtech on 2007-09-09
It's a Sondigo Inferno card.

It uses  the Oxygen HD CMI8788 chip.

I installed Ubuntu 7.04 and I don't have sound.

I'm a new user and not sure how to proceed. 

Do I need to install a driver? Not sure how. Cmedia, the chip maker says to use ALSA - not sure how.

Help appreciated. 

Lee G.

---

### Post by linuxwizard on 2007-09-09
Look through these

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

---

### Post by Alex1770 on 2007-09-09
Does your motherboard have audio output as well as your sound card? If so then as
an experiment you could try plugging your speaker jack into the motherboard's
audio output to see if it coming through there instead (in which case the problem
is probably one of diverting it to the sound card, as opposed to working out how to
drive the soundcard's chipset).

---

### Post by goldtech on 2007-09-09
> lspci -v

...

01:07.0 Multimedia audio controller: C-Media Electronics Inc Unknown device 8788
        Subsystem: C-Media Electronics Inc Unknown device 8788
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at 9000 [size=256]
        Capabilities: <access denied>

This is a start...

---

### Post by proteo on 2007-09-11
Try the oss driver: [http://www.opensound.com/oss.html](http://www.opensound.com/oss.html)
it works for me, I have a Auzen X-Meridian (Oxygen HD CMI 8788), but it have some problems, like that the gnome volume control only works with alsa drivers, so you have to use the oss mixer, some applications only work if you manually set the oss driver, no DolbyDigital Live or DTS Neo, etc.

AFAIK, the ALSA support for the card it's still experimental. Check the oss forums for more details and info: [http://www.4front-tech.com/forum/](http://www.4front-tech.com/forum/)

---

