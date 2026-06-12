---
title: "Problem connecting Ubuntu &amp; Smart TV using HDMI."
date: 2022-07-24
forum: General Help
---

### Post by davidjj2 on 2022-07-24
I have two Ubuntu PCs, and when I try to connect either of them to my Samsung Smart TV using HDMI, all that I get on the TV is the Ubuntu 20.04 desktop, and not what is showing on my PC screen. Does anyone have any idea what might be causing this? Thanks.

---

### Post by TheFu on 2022-07-24
So, it might be seen as a 2nd monitor so the desktop has been expanded.  If you are using Xorg, not Wayland, the easiest tool to control whether the desktop is expanded or mirrored is **lxrandr**.  You'll likely need to install that tool.

Also, ensure that a standard resolution and refresh rate are selected or it will likely not be displayed at all on a TV.

---

### Post by deadflowr on 2022-07-24
It's unclear what you have done with regards to the Display settings in the Ubuntu Setting app.
You mentioned connecting the TV, but it's unclear if you just plugged them together or if you applied the changes in the Display settings.
Or what changes you might have tried to apply.

---

### Post by dragonfly41 on 2022-07-24
When I tried connecting through HDMI port on a Sony TV I also noted the desktop image as described. I realised that it was in fact virtual workspace 2
I did not pursue my experiment further but I have now just learned in this thread about lxrandr which I have now installed through Synaptic. I will try again some time in next day or so. My question is how to expand the size of the HDMI view on TV screen and push audio from PC to TV. i am trying to help out a family member who has Tinnitus and I have found some relaxing images/audio.  I download from YouTube (4K YouTube to MP3) and play audio through VLC media player. I have purchased Bluetooth wireless headphones (necklace type) which works nicely. But as yet no relaxing video..

---

### Post by ajgreeny on 2022-07-24
For the sound over HDMI you probably need to go to the pulseaudio volume control, configuration tab and ensure the HDMI output you need is enabled. 
There will be several different HDMI output option if your machine is like mine so try several of them starting with the basic stereo version; that is what I use.

---

### Post by SeijiSensei on 2022-07-25
I would use the system settings to disable the laptop screen entirely. Alternatively you should be able to make the TV a mirror of the laptop. I use Kubuntu, and I manage multiple displays using System Settings. Never needed lxrandr.

I also use System Settings to manage the audio. In the past I've occasionally had to install **pavucontrol** to manage the various inputs and outputs, but modern KDE has all that built into the settings.

---

### Post by grahammechanical on 2022-07-25
On Ubuntu 20.04 I go to System Settings>Sound>Output Device and select HDMI/Display port instead of Onboard Audio.

System Settings>Screen Display give three settings. Join: Mirror and Single Display.

Regards

---

### Post by davidjj2 on 2022-07-26
Thanks very much grahammechanical, that seems to have sorted it. I had no idea the "Join/Mirror/Single Display" screen even existed, because of course it only appears when the HDMI cord is plugged in!  The Mirror setting did the trick.
Best wishes.

---

### Post by tea for one on 2022-07-26
> **davidjj2 said:**
> Thanks very much grahammechanical, that seems to have sorted it. I had no idea the "Join/Mirror/Single Display" screen even existed, because of course it only appears when the HDMI cord is plugged in!  The Mirror setting did the trick.
Best wishes.
It is beneficial to mark the thread as solved to help other forum members/searchers.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

