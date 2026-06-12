---
title: "[SOLVED] S/PDIF Problem"
date: 2016-01-18
forum: General Help
---

### Post by jonathan90 on 2016-01-18
I've been having a problem with my sound output (on my laptop) recently. I find that whenever I unplug my headphones, the sound output switches to S/PDIF. Anyone know what's going on? I recently plugged an HDMI cable in to set up a dual monitor display, though, but I'm not sure if that is relevant. Thanks!

---

### Post by jonathan90 on 2016-01-19
Bump

---

### Post by QDR06VV9 on 2016-01-19
What is the out put of this in the terminal
```
sudo aplay -l[COLOR=#111111][FONT=Ubuntu] [/FONT][/COLOR]
```

---

### Post by jonathan90 on 2016-01-20
Here's the output

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC665 Analog [ALC665 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC665 Digital [ALC665 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by QDR06VV9 on 2016-01-20
If you are not using the S/PDIF and I doubt that you are,.. you can disable(mute) that in alsamixer by typing 
```
sudo alsamixer
```

Choose the card by pressing the <F6> key borad
Then navigating using the numpad arrow left or right and when you get to S/PDIF slider just press <m> to mute..
A better method is to use the pulseaudio volume contorl.
```
sudo apt-get install pavucontrol 
```  (if not alredy installed)
Then go to your menu and to Sound & Video and select PulseAudio Volume Control.
You should have tabs at the top..Navigate to the Congiuration tab
You may have a couple of options there
If HDMI is there leave it as is and select the [ALC665 Analog]
And make sure it shows "Analog Stereo Duplex"

---

### Post by jonathan90 on 2016-01-20
I installed pavucontrol and it seems to be working now! Thanks!!!

---

