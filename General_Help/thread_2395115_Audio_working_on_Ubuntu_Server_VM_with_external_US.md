---
title: "Audio working on Ubuntu Server VM with external USB audio adapter"
date: 2018-06-26
forum: General Help
---

### Post by abhiarora on 2018-06-26
I have a VM running Ubuntu Server 16.04. I am trying to get it to play an audio file over a UGreen USB Audio adapter, specifically this one: [https://www.ugreen.com/product/UGREEN_USB_Stereo_Audio_Adapter_for_3_5mm_Headphone-en.html#ad-image-0](https://www.ugreen.com/product/UGREEN_USB_Stereo_Audio_Adapter_for_3_5mm_Headphone-en.html#ad-image-0). ALSA and PulseAudio is set up.

Running *aplay -l* returns:

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 0: Generic Analog [Generic Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Device [USB Audio Device], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
I have also set the USB Audio Device as the default sink in pulseaudio with *pacmd*:

```
$ pacmd stat
Memory blocks currently allocated: 1, size: 63.9 KiB.
Memory blocks allocated during the whole lifetime: 451335, size: 1.1 GiB.
Memory blocks imported from other processes: 0, size: 0 B.
Memory blocks exported to other processes: 0, size: 0 B.
Total sample cache size: 0 B.
Default sample spec: s16le 2ch 44100Hz
Default channel map: front-left,front-right
**Default sink name: alsa_output.usb-C-Media_Electronics_Inc._USB_Audio_Device-00.analog-stereo**
Default source name: alsa_input.usb-C-Media_Electronics_Inc._USB_Audio_Device-00.analog-mono
Memory blocks of type POOL: 1 allocated/223545 accumulated.
Memory blocks of type POOL_EXTERNAL: 0 allocated/0 accumulated.
Memory blocks of type APPENDED: 0 allocated/0 accumulated.
Memory blocks of type USER: 0 allocated/0 accumulated.
Memory blocks of type FIXED: 0 allocated/193538 accumulated.
Memory blocks of type IMPORTED: 0 allocated/34252 accumulated.
```

Using mpg123 to play the audio file with *-o pulse* or *-o openal* as an option does not output the audio to the speakers. I have tried other players as well.

The exact same configuration however, when done on another machine I have access to does output the audio to the speakers. That machine is running Ubuntu Desktop 16.04 (not on a VM). I am unable to determine what the issue is. Any insight would be great help.

---

