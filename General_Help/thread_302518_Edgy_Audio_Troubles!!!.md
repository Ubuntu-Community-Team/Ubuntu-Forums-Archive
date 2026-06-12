---
title: "Edgy Audio Troubles!!!"
date: 2006-11-18
forum: General Help
---

### Post by olieviya on 2006-11-18
I am having difficulty setting up my mike to work with skype, or to work at all really. If i use OSS i can record my voice through the mike only when shouting at the top of my lungs - anything else is so low that you can't hear it. With ALSA it doesn't even work. Basically what I want and can't manage is to get my mike up and running with Ubuntu AND my laptop has a volume up/down dial on the side near the keyboard that I want to be able to use but it's not working.

Both of these work perfectly in winXP so it's not their fault.

For the dial I have tried finding and using it via the Keyboard shortcuts and  for the mike I have been messing about with the gnome volume control but cannot seem to work out anything.

Help would be very appreciated.

---

### Post by olieviya on 2006-11-18
[COLOR="Gray"]**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC880 Digital [ALC880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/COLOR]

---

### Post by ouilsen on 2006-11-18
Maybe you have to switch the "mic boost" on (same as in windows). In gnome, check your preferences in your audio mixer. There should be a "mic boost" option. Finally you can switch it on/off under the "switches" tab.

Edit: Just checked... Only the ALSA mixer has the "mic boost" switch. And also check that your "microphone capture" channel is switched on and set correctly.

---

### Post by olieviya on 2006-11-18
> **ouilsen said:**
> Maybe you have to switch the "mic boost" on (same as in windows). In gnome, check your preferences in your audio mixer. There should be a "mic boost" option. Finally you can switch it on/off under the "switches" tab.

Edit: Just checked... Only the ALSA mixer has the "mic boost" switch. And also check that your "microphone capture" channel is switched on and set correctly.

Where? ](*,) [[IMG]http://img165.imageshack.us/img165/585/screenshotvolumecontrolon4.png[/IMG]](http://imageshack.us)

---

### Post by silentb on 2006-11-18
Terminal -> alsamixer :)

---

### Post by ouilsen on 2006-11-18
I can switch to the alsa mixer under "File -> Device". The "mic boost" and "microphone capture" should then be under "Edit->Preferences". Switch both of them on.

---

### Post by olieviya on 2006-11-19
> **ouilsen said:**
> I can switch to the alsa mixer under "File -> Device". The "mic boost" and "microphone capture" should then be under "Edit->Preferences". Switch both of them on.



Ok, it's either too early for my brain to be working properly or it doesn't exist...
With ALSA on this is what I can see... isn't the mic boost supposed to be in there?



[[IMG]http://img175.imageshack.us/img175/4306/screenshotvolumecontrolle1.png[/IMG]](http://imageshack.us)

---

### Post by olieviya on 2006-11-23
Still having trouble with mike - very very low volume, anybody??????

---

