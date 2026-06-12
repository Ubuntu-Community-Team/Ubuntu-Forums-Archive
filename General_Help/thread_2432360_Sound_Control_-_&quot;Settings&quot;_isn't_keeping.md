---
title: "Sound Control - &quot;Settings&quot; isn't keeping my device selection"
date: 2019-12-01
forum: General Help
---

### Post by andrew-thecallums on 2019-12-01
All:  I am a very long time Ubuntu user, and have been largely self-sufficient until a recent problem has me stumped.

I have a desktop machine with an Intel onboard sound, I also have a Xonar soundcard (it's amazing for music) and a new HDMI monitor.  I am running stock Ubuntu 19.10.

The issue I am having is that my system keeps defaulting the output device to the HDMI 'channel'.  I have to go in every time I log in to set it back to the Analog signal on the soundcard.  This allows my Apple keyboard to manage the volume.

I can't seem to figure out why my choice isn't remaining as the setting.

Any help or suggestions are most welcome!

Thanks.

---

### Post by CatKiller on 2019-12-01
> **andrew-thecallums said:**
> 
I can't seem to figure out why my choice isn't remaining as the setting.

What you've been changing is the device that is currently being used. What you want to change is the default device. The options in Gnome are limited compared to those in other desktop environments, but installing pavucontrol should help you to do it.

---

### Post by andrew-thecallums on 2019-12-04
CatKiller (I am sure there is a story behind your user name):  Many thanks.  I installed pavucontrol and it looked like I had two devices set as output, so I turned off the HDMI and hopefully this will work.  Really appreciate your help.

---

### Post by CatKiller on 2019-12-04
> **andrew-thecallums said:**
> CatKiller (I am sure there is a story behind your user name): 

There is, but it's terribly dull.

> Many thanks.  I installed pavucontrol and it looked like I had two devices set as output, so I turned off the HDMI and hopefully this will work.  Really appreciate your help.

Fingers crossed.

The "fallback" device is the default one for PulseAudio. Desktop environments that aren't Gnome also let you just drag-and-drop the list of audio devices to set your preferences.

---

### Post by andrew-thecallums on 2019-12-05
Well, I must be doing something wrong.  I can't seem to get these settings to stick.  I log in later, and the HDMI output device is again active, and actually the default. 

Anyone have an idea as to how to turn this off?

Thanks again.

---

### Post by CatKiller on 2019-12-05
On the Configuration tab there should be a dropdown box for each device to set the profile. One of the profiles is "Off." That should work to disable all the devices that you don't want to use. If it doesn't, I don't have any other ideas.

---

