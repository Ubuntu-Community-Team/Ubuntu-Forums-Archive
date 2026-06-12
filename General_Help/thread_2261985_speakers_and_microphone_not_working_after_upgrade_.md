---
title: "speakers and microphone not working after upgrade (ubuntu 14.04)"
date: 2015-01-22
forum: General Help
---

### Post by louisJ on 2015-01-22
I updated my ubuntu 14.04 system with
  
sudo apt update
sudo apt upgrade


  and now my external microphone doesn't work anymore (it was working  yesterday and its works now on other devices) and I need it for work. My sound (speakers or external headset) doesn't work neither.
  When I open the sound settings, I don't see the input signal.
  
Can you please help me ?

  
my laptop is a Lenovo Thinkpad t400

  sro-ThinkPad-T400:~$ sudo aplay -l

**** Liste des Périphériques Matériels PLAYBACK ****
carte 0: Intel [HDA Intel], périphérique 0: CX20561 Analog [CX20561 Analog]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 0: Intel [HDA Intel], périphérique 1: CX20561 Digital [CX20561 Digital]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0

sro-ThinkPad-T400:~$ pactl list short sinks

2   alsa_output.pci-0000_00_1b.0.iec958-stereo  module-alsa-card.c  s16le 2ch 48000Hz   SUSPENDED


$ cat /proc/asound/cards

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfc020000 irq 49
29 [ThinkPadEC     ]: ThinkPad EC - ThinkPad Console Audio Control
                      ThinkPad Console Audio Control at EC reg 0x30, fw 7VHT16WW-1.06

---

### Post by oldrocker99 on 2015-01-22
Install pavucontrol, and make sure that your sound isn't muted, which can sometimes happen:

```
sudo apt-get install pavucontrol
```

---

### Post by louisJ on 2015-01-22
Thanks, I just installed pavucontrol. And nothing is muted. 

I did this :
killall pulseaudio; rm -r ~/.config/pulse/* ; rm -r ~/.pulse*; ~/.config/pulsewait ten seconds, then run this:   
pulseaudio -k 

Now I have the sound, but the external microphone is still not working (I have checked it on another device and the microphone itself works perfectly).

---

### Post by louisJ on 2015-01-26
Please help  !!!

---

