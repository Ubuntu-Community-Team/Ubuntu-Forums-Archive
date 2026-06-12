---
title: "Audio input (internal/external mics) not working | new 18.04 install on Acer Swift 3"
date: 2019-02-04
forum: General Help
---

### Post by xgieryn on 2019-02-04
Fresh install of Ubuntu 18.04. No audio input from onboard mic or  headphone/mic combo (these both work fine when I boot same machine, Acer  Swift 3 SF314-54, via Windows 10), alsamixer showing "sound device has  no capture controls" (EDIT: see solutions tried, I can get capture control on USB Audio Adapter/ Sound Card).

I don't know if it's related, but I installed "Pulse Audio Shortcuts"  extension and when I try to turn it on in the extensions section of the  GNOME Tweaks program I see a yellow warning triangle with "Error loading  extension" next to it. I don't appear to have gstreamer-properties  command, either, even though I believe PulseAudio comes with 18.04?

Anyways, would be very grateful for approaches to solve this, thanks!

Here's my input and output settings:

   ```
 ~$ arecord -l
    **** List of CAPTURE Hardware Devices ****
    card 0: PCH [HDA Intel PCH], device 0: ALC256 Analog [ALC256 Analog]
    Subdevices: 0/1
    Subdevice #0: subdevice #0
    card 0: PCH [HDA Intel PCH], device 2: ALC256 Alt Analog [ALC256 Alt Analog]
    Subdevices: 2/2
    Subdevice #0: subdevice #0
    Subdevice #1: subdevice #1
```

    ```
~$ aplay -l
    **** List of PLAYBACK Hardware Devices ****
    card 0: PCH [HDA Intel PCH], device 0: ALC256 Analog [ALC256 Analog]
    Subdevices: 0/1
    Subdevice #0: subdevice #0
    card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
    Subdevices: 1/1
    Subdevice #0: subdevice #0
    card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
    Subdevices: 1/1
    Subdevice #0: subdevice #0
    card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
    Subdevices: 1/1
    Subdevice #0: subdevice #0
    card 0: PCH [HDA Intel PCH], device 9: HDMI 3 [HDMI 3]
    Subdevices: 1/1
    Subdevice #0: subdevice #0
    card 0: PCH [HDA Intel PCH], device 10: HDMI 4 [HDMI 4]
    Subdevices: 1/1
    Subdevice #0: subdevice #0
```

[ALSA settings screenshot]([https://www.dropbox.com/s/zz5gyp6bokzt2s3/alsa-issue-0_delete_.png?dl=0](https://www.dropbox.com/s/zz5gyp6bokzt2s3/alsa-issue-0_delete_.png?dl=0))

[ALSA "no capture device setting" screenshot]([https://www.dropbox.com/s/vs5w08w54n6caq2/alsa-issue-1_delete_.png?dl=0](https://www.dropbox.com/s/vs5w08w54n6caq2/alsa-issue-1_delete_.png?dl=0))

**Couple things I've tried**:

- installed pulseaudio volume controller, checked the input Port,  which only has one option, "Analog input". Tried messing with the  configuration but it's not working on the setting I believe it should be  set to, "Analog stereo duplex"

- bought a USB Audio Card (USB Audio Adapter); it ouputs audio  fine, but still no luck getting audio input. Interestingly, though, when  I plug in my headset into the microphone jack I do get some bars in  Sound > Input indicating it is receiving something. Additionally, in  AlsaMixer if I switch sound cards to USB Audio Device and then go to  'capture device', I do see a Mic with a EQ bar above it that I can  adjust, with CAPTURE in red text just below the EQ bar

---

### Post by ww5 on 2019-05-02
[SIZE=2][FONT=arial]Hi, I have the same issue on Acer Swift 3.  Have you found  a solution?
[/FONT][/SIZE]

---

