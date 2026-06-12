---
title: "sound very low"
date: 2008-05-18
forum: General Help
---

### Post by donhatem on 2008-05-18
Hi,
I'm trying since 2 weeks to resolve my problem which is a very low sound, I did all update, I reconfigure alsa... but I got the same problem, please can you help me ! 

here's all information :
ubuntu 8.04


#aplay -l
**** Liste des PLAYBACK périphériques ****
carte  0: Intel [HDA Intel], périphérique 0 : ALC880 Analog [ALC880 Analog]
  Sous-périphériques: 0/1
  Sous-périphérique: #0: subdevice #0
carte  0: Intel [HDA Intel], périphérique 1 : ALC880 Digital [ALC880 Digital]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0


#cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xffa3c000 irq 16


#lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 05)


#amixer info
Card default 'Intel'/'HDA Intel at 0xffa3c000 irq 16'
  Mixer name	: 'Realtek ALC880'
  Components	: 'HDA:10ec0880'
  Controls      : 36
  Simple ctrls  : 19

---

### Post by donhatem on 2008-05-18
up

---

