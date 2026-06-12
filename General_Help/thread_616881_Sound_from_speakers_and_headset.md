---
title: "Sound from speakers and headset"
date: 2007-11-18
forum: General Help
---

### Post by SpiritMacardi on 2007-11-18
I have a problem. Whenever I plug in my headset, which just goes into the standard speaker and mic jacks on the front of my computer, I get sound out of it, but it doesn't cut off the computer's speakers. As a result, I get feedback during voice chats and it is getting very annoying. I've tried looking at the volume controls, but to no avail. If anyone knows how I can get the computer's speakers to shut off when I plug in my headset it would be greatly appreciated.

---

### Post by fnf on 2007-11-18
That is usually a hardware problem. As far as I know, the system won't receive any signal when you plug in or take off the headset: Toggling the speakers off is the job of your computer/soundcard.

It is easy to toggle the headset and speakers though: use 'alsamixer' (from the terminal) and play with the channels a bit. The actual number and type of channels will differ with each soundcard, but usually Front, Surround and Headphone are notably responsible channels.

Having gotten through that problem, it is fairly easy to create a script, which will be called when you press a key combination to toggle on and off the speakers/headphone.

---

### Post by SpiritMacardi on 2007-11-18
I know it's not a hardware problem, because the speakers cut out when I use the headset in Vista. And I already tried the alsamixer controls, but they didn't work.

---

### Post by fnf on 2007-11-18
Under Windows there probably is a system service polling the device's state through the device driver. I haven't seen a standard kernel function for this sort of stuff, perhaps it must be implemented per-driver/device.

What channels have you got with alsamixer?. Have you tried (un)muting them all?. What is your sound card?.

I like toggling them manually though (through a 1-liner script), plugging the headset in and out is too much of a hassle.

---

### Post by Benchrest on 2008-04-10
Do you h ave a resolution for this problem yet? I am also having the problem. Works fine with Vista. I will keep looking at alsa

---

