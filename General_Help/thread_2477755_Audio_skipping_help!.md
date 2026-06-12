---
title: "Audio skipping help!"
date: 2022-08-06
forum: General Help
---

### Post by libertyspike138 on 2022-08-06
I recently installed 22.04 to a GA-B150M-DS3H motherboard that according to lspci uses an Intel Corporation 100 Series/C230 Series Chipset Family HD Audio Controller (rev 31). My audio keeps skipping and when it does I notice that the output device in gnome-settings flashes. I tried searching for this but really only found 1 post affecting somebody else with no solutions but just generic advice to do a bug report to rhythmbox but this is not a rhythmbox issue. [https://askubuntu.com/questions/1420658/audio-and-video-keep-skipping-without-any-reason-in-ubuntu-22-04](https://askubuntu.com/questions/1420658/audio-and-video-keep-skipping-without-any-reason-in-ubuntu-22-04)

---

### Post by libertyspike138 on 2022-08-06
I also find it important to note that after a reboot it is gone temporarily but I know it will be back as I have experienced it multiple times and initially thought it was related to another problem where if I use the DVI-D the screen may randomly go black and is triggered by certain images on the screen. Using DVI-I or DisplayPort solves my blackout issue but there is also this. It makes me think that something is interrupting the bus with the flashing of my output device and all. I have my gnome-settings -> Power set to performance.

---

### Post by libertyspike138 on 2022-08-06
So I believe this is a bug in how it detects if you have anything plugged into any of the audio jacks. It is like it is thinking that the speakers are unplugged for milliseconds and then comes back. Is there some way to disable this like it used to be on computers before jack detection was a thing and just have it make all jacks constantly available whether anything is plugged in or not?

---

### Post by libertyspike138 on 2022-08-06
I also wanted to mention that this affects Linux only. If I boot into MacOS or Windows the problem does not exist.

---

### Post by libertyspike138 on 2022-08-06
So I found a solution here. [https://www.reddit.com/r/linuxquestions/comments/una0ko/disable_sound_jack_detection_while_enabling_sound/](https://www.reddit.com/r/linuxquestions/comments/una0ko/disable_sound_jack_detection_while_enabling_sound/)

So far it seems to be functioning fine. If the problem comes back I will leave an update.

---

### Post by libertyspike138 on 2022-08-08
So I tried to install another distro on a separate drive and the distro decided that it was going to rewrite the partition table of not only the drive it was supposed to install to but also my main nvme that has my EFI & Ubuntu installation on ZFS... There was no recovering that... Anyway I have a fresh installation and I have replicated the steps taken but apparently my audio is still messed up! Also this time around my max resolution is 1360x768 in xorg and 1024x768 in Wayland... I have the latest proprietary tested nVidia 470 driver installed on a GTX 770. Starting to think that Micro$oft guys must be working at Canonical or something... I had the same video card, no audio skip etc. in a different board running 20.04 instead of 22.04 and it would do 1080p on both of my monitors in my mirror...
#rant:end

---

### Post by libertyspike138 on 2022-08-08
This time around the only difference I notice is that in gnome-settings my audio device is not flashing when the sound skips.

---

### Post by libertyspike138 on 2022-08-08
Well I tried this and I will warn you that it did not work but also removing it removed gdm3 & ubuntu-desktop so if you're not familiar with opening a new tty and reinstalling missing items from the terminal to get back into your system, don't waste your time. [https://trendoceans.com/enable-pipewire-and-disable-pulseaudio-in-ubuntu/](https://trendoceans.com/enable-pipewire-and-disable-pulseaudio-in-ubuntu/)

---

### Post by libertyspike138 on 2022-08-08
Strange how if I plug into the headphone jack it seems to be okay... Would make you think it's a hardware problem, but once again, I boot into Windows or MacOS and my line output is fine...

---

