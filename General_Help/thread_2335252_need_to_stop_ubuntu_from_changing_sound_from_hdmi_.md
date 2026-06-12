---
title: "need to stop ubuntu from changing sound from hdmi to analog"
date: 2016-08-26
forum: General Help
---

### Post by rustin-2 on 2016-08-26
first thing i did was terminal command "aplay -l", all this did is make me more confused.  why do i have 3 different HDMI listed?  and, why is everything listed as card 0?  thank you.

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC269VC Analog [ALC269VC Analog]
  Subdevices: 1/1
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

---

### Post by TheFu on 2016-08-29
In programming, we start counting from 0.  You'll see the first choice almost everywhere as "0".

I'm just guessing (I have 3 HDMI devices too) - think they are either for different resolutions supported or for different digital audio output type supported.

I think there is a way to set the default using pulse-audio.

Welcome to the forums.

---

### Post by rustin-2 on 2016-08-30
yes, pulseaudio does have HDMI as default.  the trouble is ubuntu just changes it to analog audio.  i thought is was happening when screen blanks.  i disabled screen blank and it no longer blanks the screen, but it still changes audio.  as to why and how to make it stop, it's way outside my knowledge of ubuntu.  thanks for helping.

---

### Post by TheFu on 2016-08-30
Have you tried these ideas?  [https://askubuntu.com/questions/14077/how-can-i-change-the-default-audio-device-from-command-line](https://askubuntu.com/questions/14077/how-can-i-change-the-default-audio-device-from-command-line)

---

### Post by rustin-2 on 2016-08-30
pulseadio has HDMI as default.  if i have computer on and i walk away, after a while (ten min i think) sound changes to analog.  i know how to change it back, i just want to know how to stop it from changing.

---

### Post by TheFu on 2016-08-30
That link in #4 above provides answers for how to change AND set the default audio output device.  Worked for me.
For all the official documentation: [https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/](https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/)  There isn't anything more than what is there.  
The Ubuntu Desktop Guide might be helpful as well: [https://help.ubuntu.com/stable/ubuntu-help/media.html](https://help.ubuntu.com/stable/ubuntu-help/media.html) is the Sound and Media link.

That's all I know. Sorry.

---

