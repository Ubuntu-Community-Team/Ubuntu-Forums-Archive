---
title: "no built-in analog audio stereo in 14.04"
date: 2016-10-26
forum: General Help
---

### Post by marsdenf on 2016-10-26
using xubuntu 14.04 on new desktop (a few months old).  In pulse audio volume control, there is no entry for " built-in analog audio stereo", only entries "hda nvidia", "audio codec", "2.0 root hub" (my digital mike) and "webcam c270" (my webcam mike).  I have digital speakers with usb connections and the sound is fine.  When I turn off the speakers, the entry "audio codec" disappears.  Speakers have optional analog connection (jack) but it doesn't work. Convention analog speakers also don't work.  Analog microphones (jack) don't work, and neither do jack headphones on the desktop. Webcam mike works, but it is usb connected. The only way headphones work is if I plug them into the jack on the back of the monitor (which is hdmi connected to desktop) and switch to "hda nvidia" in volume control.  Here is the output of aplay -l


marsdenf@marsdenf-Z170X-Gaming-3:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: DAC [USB Audio DAC], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
marsdenf@marsdenf-Z170X-Gaming-3:~$ 


   Does the desktop have the necessary hardware for built-in analog audio stereo, and if so, how to get it in pavucontrol?

---

### Post by marsdenf on 2016-10-27
I forgot that I posted the same problem some months ago, and it was suggested that I upgrade ALSA and LTS enablement stacks.  I have done both and it didn't work.

---

### Post by marsdenf on 2016-10-27
The problem solved itself.  The computer has two other hard drives, and I just installed xubuntu 16.04 and ubuntu mate 16.04 on them, did update-grub on all 3 drives, and now the one with xubuntu 14.04 has built-in audio.  I don't know why.

---

