---
title: "No sound from built in speakers on ASUS EXPERTCENTER AIO E5402W"
date: 2023-01-07
forum: General Help
---

### Post by ivan3666 on 2023-01-07
Hello everyone,

First of all I wish you all the best in new year. After over 20 years in Windows and Mac environment, it is time to return to roots.

I have installed fresh copy of Ubuntu 22.04.1 LTS on my ASUS EXPERTCENTER AIO E5402W I have no sound coming from the speakers. Bluetooth headset is working fine. I have tried all the solutions I have found on various forums (don't ask to remember them all), but no luck. AlsaMixer seems to show all the right values. PulseAudio Volume Control is showing as the sound is playing-that blue line is moving. Screenshots attached.

Any help or step by step guide is appreciated. I will sure know to respect your time and efforts and will send some beer or lunch money. Thank you.

Ivan

---

### Post by TheFu on 2023-01-08
First, there are different drivers for the motherboard audio chips and the GPU audio chips. The
```
inxi -A
```
command will show what the kernel sees and spell out the driver installed. Often, they both use the same named driver.

ALSA is the core sound management, but since PulseAudio was added to most Ubuntu systems around 2016, that is the only tool end users should need to touch.  The 'pavucontrol' provides the most complete interface.  Inside that tool, start with the far right tab and work left, enabling and disabling all but the exact hardware  you plan to use.  

If you want analog audio, then be certain you don't pick digital outputs for that specific device.  Don't forget to disable/off the hardware you don't want used, at least for now. Later, as you become more familiar with this interface, you can have 10 different devices enabled, if that's your choice. For now, we just want the single device that isn't working, which you want, enabled.

I'm not a fan of the interface, but it does put the tabs we need to touch the most often to the far left, so it does make sense. Alas, the initial configuration starts in the far right, Hardware, tab.

Anyway, give that a shot and hopefully, you'll be able to report success.  
There are 3 groups of tabs (that's my way of thinking, nothing official)
a) volume for outputs, microphone inputs sensitively; use this on a per-application input/output need.
b) gain for outputs, gain for microphone inputs  Generally, I set these to 75% or 100% values and don't touch them. The goal is to have them as high as possible, but not so high that distortion happens for either the inputs or the outputs.
c) Hardware

---

