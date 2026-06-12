---
title: "Automaticly switch to USB headphones when plugged"
date: 2008-01-22
forum: General Help
---

### Post by grof on 2008-01-22
I have USB headphones, so I want to ALSA automatically switch to USB headphones when pluged in, and if plug out then switch back to speakers.

This works in Windows normally, so is it possible in my Ubuntu 7.10??

---

### Post by gvartser on 2008-01-22
Maby this will help.

1) Double click on the speaker icon in the task bar.

2) Click on the "Switches tab"

3) Select "Headphone Jack Sense"

Best Regz,
/G

---

### Post by edm1 on 2008-01-22
I'm afraid its not so easy in 7.10, it can be done manually through System>Pref>Sound. We're all excited about 8.04 and the implementation of PulseAudio which will make stuff like this alot easier.

---

### Post by grof on 2008-01-22
Ah, thanks.

I'm waitng on Hardy...

---

### Post by grof on 2008-01-23
> **gvartser said:**
> Maby this will help.

1) Double click on the speaker icon in the task bar.

2) Click on the "Switches tab"

3) Select "Headphone Jack Sense"

Best Regz,
/G


I do not have this option in my Volume Applet 2.20

---

### Post by heindsight on 2008-01-23
I've never tried this and I don't have USB headphones so I couldn't even if I wanted to, but it would be  easy to write a udev rule to run a script that somehow (that's the tricky part I guess) gets ALSA to switch to the USB headphones, each time they're plugged in.

---

### Post by grof on 2008-01-23
I found this:

[http://alsa.opensrc.org/index.php/Hotplugging_USB_audio_devices_%28Howto%29](http://alsa.opensrc.org/index.php/Hotplugging_USB_audio_devices_%28Howto%29)

I think that will help me to make autoswitching on hotplug.

I'll try tomorrow

---

### Post by grof on 2008-01-24
Do not work :confused:

nor the hotplugging, neither change default device.

I tried udev rules, but this do not work at all.

I'm confused....

---

