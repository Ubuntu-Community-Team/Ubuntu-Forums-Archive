---
title: "How to disable/hide unused Sound deice ?"
date: 2014-07-16
forum: General Help
---

### Post by bizhat on 2014-07-16
Hi,


How do i remove unused Device from Sound.


[IMG]http://i.imgur.com/zPLLYfh.png[/IMG]


I want to remove "Digital Output (S/PDIF)" device as i am not using it. I don't know what it is. Maybe something with my motherboard, i have no use.


Then cards i have 


```

boby@fwhlin:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfb9f8000 irq 75
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfbcfc000 irq 76
boby@fwhlin:~$ 

```


How i disable/hide the device so i have only 2 device in Sound setting (i use one for speaker, other for headphone).


Thanks,


Boby

[B]Edit

[/B]I found some more info about the device  that i need to disable/hide from Sound control.

```

boby@fwhlin:/proc/asound/card0/pcm1p$ cat info 
card: 0
device: 1
subdevice: 0
stream: PLAYBACK
id: ALC892 Digital
name: ALC892 Digital
subname: subdevice #0
class: 0
subclass: 0
subdevices_count: 1
subdevices_avail: 1
boby@fwhlin:/proc/asound/card0/pcm1p$ 


boby@fwhlin:/proc/asound$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
boby@fwhlin:/proc/asound$ 

```

---

### Post by 3rdalbum on 2014-07-16
I don't think you can hide it. It's part of your motherboard and there is no benefit to hiding this device. Just pretend it's not there!

---

