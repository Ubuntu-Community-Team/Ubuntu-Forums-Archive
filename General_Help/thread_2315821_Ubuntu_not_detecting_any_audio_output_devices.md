---
title: "Ubuntu not detecting any audio output devices"
date: 2016-03-02
forum: General Help
---

### Post by squiffer on 2016-03-02
Hi everyone,

 I have just installed Ubuntu 15.10 to a new Acer E5-522G laptop, but am having difficulties in Ubuntu detecting any audio output.

 In the sounds settings, there is no selectable sound output device to select from. AlsaMixer will only show HDA ATI HDMI as a selectable sound card, and it is not showing any levels. 

I have tried updating any additional drivers, to no such luck. I have also tried reloading Alsa Mixer and restarting the laptop. 

I have done some searching, and gone through the audio troubleshooting guide but to no avail.

 I know this is limited info, but I don't want to bombard with to much information from the system which may not be relevant, in which case if anyone can help I will post as much information as I can!

What is the best approach  to get Ubuntu to activate the sound drivers needed? There was sound on the system before Ubuntu was installed, on Windows8. 

Many thanks for any help.

---

### Post by sandyd on 2016-03-03
Please post the output of the following:
```

aplay -l
lspci | grep -i audio
```

---

### Post by squiffer on 2016-03-03
Hi, 

Thanks for the reply. 

The output is as follows:

```
dave@dave-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
dave@dave-laptop:~$ lspci | grep -i audio
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio


```

Many thanks

---

### Post by squiffer on 2016-03-04
What should I be looking for from the output code?

Thanks

---

### Post by trag on 2016-03-08
Just a hunch but maybe try installing Pulseaudio,it is a better sound server and you should be able to get sound working through the Pulseaudio volume control.
good luck
Tagic

---

### Post by squiffer on 2016-03-08
Thanks for the reply. 

I could not fully work out exactly what the problem was, but what I did was re install alsamixer and pulseaudio, updated Ubuntu and searched for additional drivers. At first, the AMD Kabini audio driver was unselectable, saying "this device is not working", but after a restart I managed to get audio out. 

I dont know of this had anything to do with it, but on Software and Updates, I enabled pre-release updates. 

Thanks again

---

