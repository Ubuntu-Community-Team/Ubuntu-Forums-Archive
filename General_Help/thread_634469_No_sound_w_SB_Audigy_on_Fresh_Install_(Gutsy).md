---
title: "No sound w/ SB Audigy on Fresh Install (Gutsy)"
date: 2007-12-07
forum: General Help
---

### Post by h0lix on 2007-12-07
Greetings-

I just recently upgraded to gutsy from dapper. (I tend to wait for a release to be out for a while before upgrading)

I had anticipated having issues with my graphics card but much to my surprise gutsy loaded my card perfectly.

However, i have no sound. 

I have been browsing through many different threads discussing this issue and still cant manage to find something what is causing my sound not to work. 

when i run:

```
aplay -l
```

i get:

c```
ard 0: Audigy [Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 0: Audigy [Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy [Audigy 1 [SB0090]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 1: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

card 0: is my sound card that worked fine with dapper and it is the one i want to use. 

I know there has been a lot of discussion on this topic but i cant seem to find what i need to get my sound working. 

any insight would be greatly appreciated. 

thanks in advance!

---

### Post by linuxwizard on 2007-12-07
Have you tried this
check that your switches are set correctly - for instance that if you use the analog output the analog switch is set ON or that the digital or S/PDIF switch is set OFF.

To get to the switches > right click speaker icon on gnome panel > open volume control > click on switch tab > you could have 3 or 4 settings there look for the one analog/digital unmark it > try playing something

---

### Post by Jimmey on 2007-12-07
I had the same problem. You need to set the default sound device to your audigy. Search this forum for the sound thread.

EDIT

I can't find the thread, actually, don't know where it's gone! Let me try to find the instructions. 

For now, search "sound" at [http://help.ubuntu.com]("http://help.ubuntu.com")

---

### Post by h0lix on 2007-12-08
> **linuxwizard said:**
> Have you tried this
check that your switches are set correctly - for instance that if you use the analog output the analog switch is set ON or that the digital or S/PDIF switch is set OFF.

To get to the switches > right click speaker icon on gnome panel > open volume control > click on switch tab > you could have 3 or 4 settings there look for the one analog/digital unmark it > try playing something

Thank you so much! I disabled the "Audigy Analog/ Digital Output Jack" in switches and the sound instantly started working.

Excellent.

---

### Post by h0lix on 2007-12-08
Well, i had the sound working fine but as soon as i restarted the device selected for sound switched to my mobo sound card. Changing it back to the audigy does nothing because as soon as i do that there are no "switches" options. 

Im going to continue tinkering with it since i found where the issue is.


meanwhile, any other ideas?

---

### Post by linuxwizard on 2007-12-08
Look at the bottom of this page for  Configuring default soundcards / stopping soundcards from switching

[https://help.ubuntu.com/community/SoundTroubleshooting#head-72023a784829d5d128546a6092d67062ab50dfea](https://help.ubuntu.com/community/SoundTroubleshooting#head-72023a784829d5d128546a6092d67062ab50dfea)

---

### Post by h0lix on 2007-12-09
hmm. no luck after restart. here is what i did:

```
cat /proc/asound/modules
```

returns:

```
 0 snd_via82xx
 1 snd_emu10k1

```

then: 

```
sudo gedit /etc/modprobe.d/alsa-base
```

added in:

```

options snd-snd_emu10k1 index=0
options snd-snd_via82xx index=1
```

Still gives via82xx as default when i check in alsamixer.  I appreciate the help linuxwizard, any other suggestions?

---

