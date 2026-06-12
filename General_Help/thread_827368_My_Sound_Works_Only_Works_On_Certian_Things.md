---
title: "My Sound Works Only Works On Certian Things"
date: 2008-06-12
forum: General Help
---

### Post by morbidxbean on 2008-06-12
Im wondering whats wrong here, whats going on is that i will have sound when the log in screen comes up and when i do that hardware testing thing i will have sound but when i try to listen to a music cd, or watch youtube videos i get no sound at all...whats going on?:confused:

---

### Post by morbidxbean on 2008-06-12
im wondering whats wrong here, whats going on is that i will have sound when the log in screen comes up and when i do that hardware testing thing i will have sound but when i try to listen to a music cd, or watch youtube videos i get no sound at all...whats going on?

---

### Post by breadbin on 2008-06-12
try running some of the apps that you are having trouble with from the terminal and see if any error messages come up? I had a problem where I had sound in gnome - cds and video etc but not games and the like and its probably something using the audio device like ARTS or something like that. pulseaudio maybe? might shed a little more light on your problem

---

### Post by Vivaldi Gloria on 2008-06-12
Hardy uses the new pulseaudio and everybody is having problems with something. I fixed mine following the guides:

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

---

### Post by morbidxbean on 2008-06-12
> **breadbin said:**
> try running some of the apps that you are having trouble with from the terminal and see if any error messages come up? I had a problem where I had sound in gnome - cds and video etc but not games and the like and its probably something using the audio device like ARTS or something like that. pulseaudio maybe? might shed a little more light on your problem


How exactly do I run programs from terminal?

---

### Post by Vivaldi Gloria on 2008-06-12
> **morbidxbean said:**
> How exactly do I run programs from terminal?

 To open a Terminal do as follow:

    *       Choose Applications &#8594; Accessories &#8594; Terminal;
    *       Or press Alt+F2 and type gnome-terminal.

See

[https://help.ubuntu.com/8.04/basic-commands/C/](https://help.ubuntu.com/8.04/basic-commands/C/)

To start a program in the terminal just write its name and press enter. For example try gedit.

---

### Post by morbidxbean on 2008-06-12
> **Vivaldi Gloria said:**
> Hardy uses the new pulseaudio and everybody is having problems with something. I fixed mine following the guides:

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)



I did the second guide...and still dosnt work

---

### Post by Trollslayer on 2008-06-12
Can you give us more information? PC hardware, type of audio output (analogue, SPDIF etc.) and the results of 'aplay -l'?

---

### Post by morbidxbean on 2008-06-12
Decided to plug my Speakers onto my onboard sound card, it works!  However the sound doesn't seem to go that loud what could be the problem here?

---

### Post by morbidxbean on 2008-06-12
> **Trollslayer said:**
> Can you give us more information? PC hardware, type of audio output (analogue, SPDIF etc.) and the results of 'aplay -l'?

sure


```
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [SBLive! [CT4620]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 1: Live [SBLive! [CT4620]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Live [SBLive! [CT4620]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

