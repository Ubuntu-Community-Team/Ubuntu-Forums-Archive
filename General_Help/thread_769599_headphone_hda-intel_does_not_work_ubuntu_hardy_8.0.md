---
title: "headphone hda-intel does not work ubuntu hardy 8.04"
date: 2008-04-26
forum: General Help
---

### Post by krantix on 2008-04-26
Hi! Since I've updated my Gutsy to Hardy my headphone do not work anymore. Before I had to run the system with acpi=off to get sound working (hda-intel card, conexant venice). Now it works out of the box, but headphone do not.

When I plug-in the jack I can ear the sound only if I plug it in about half the way in... when it's completely in it does not work.

Laptop is a toshiba satellite pro P100.

Everything was fine with Gutsy, now it does not work even with ACPI=OFF

:-(

---

### Post by JS Lemming on 2008-04-26
Same problem here. I have a Toshiba Satellite A135-S4527.

---

### Post by tuskpc on 2008-04-27
Same problem here.  This only highlights how shoddy Toshiba Satellite - in my case P105-S6147 - really is manufactured.  You would think the company would be trying to help the Linux community in order to prevent bad publicity.  :-({|=

---

### Post by sparrowkc on 2008-04-27
Have you tried messing with levels/mutings in alsa mixer?  
Type alsamixer into a terminal to get to it.  I had to mute an "external amplifier" to get my sound working...

---

### Post by krantix on 2008-04-27
alsa mixer everything up... still no sound from the headphones. The strange thing is that it worked in gutsy!

---

### Post by fimbulvetr on 2008-04-27
They're not suggesting you put everything "up" in alsamixer, but to unmute your hardware devices. In alsamixer, below each bar (And even below devices with no adjustable bar!), there's a little box that can be in one of two states:

00 or MM

MM means mute. Use your arrow keys to navigate to the device with an MM, then press your "m" key to toggle mute. I had this same issue and it was resolved by unmuting the device IEC958.

---

### Post by Chii on 2008-04-27
Having the same issue, with a toshiba p100-st9752... it's funny how it works if it's half way plugged in.  This being because it's not relying on the "headphone" slider but still on the main one >.<

---

### Post by krantix on 2008-04-27
everything up and unmuted. Still no sound. It seems like the toshiba p100 do not have digital SP/DIF output from the headphone jack, maybe that's the problem??? 

I've subscribed to this bug on launchpad

see here [https://bugs.launchpad.net/ubuntu/+bug/218817](https://bugs.launchpad.net/ubuntu/+bug/218817)

---

### Post by sparrowkc on 2008-04-27
Just to be clear, I had to mute something that was un-muted for mine to work.

---

### Post by AlanR8 on 2008-04-27
Had a similar problem with my Sony running Gutsy but it's resolved in Hardy! I came across this on these forums to solve the problem in Gutsy:

Code

> Edit /etc/modprobe.d/alsa-base (sudo gedit /etc/modprobe.d/alsa-base) and add this in the bottom of it

options snd-hda-intel model=vaio

then do this:

sudo apt-get install linux-backports-modules-$(uname -r)

If you change the vaio for default it might help.

At your own risk but it worked for me.

---

