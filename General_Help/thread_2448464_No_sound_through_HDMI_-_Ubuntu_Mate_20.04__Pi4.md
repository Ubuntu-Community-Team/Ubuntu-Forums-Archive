---
title: "No sound through HDMI - Ubuntu Mate 20.04 / Pi4"
date: 2020-08-08
forum: General Help
---

### Post by adambegood on 2020-08-08
I've installed Ubuntu Mate 20.04 on my Pi 4, and I don't seem to have HDMI sound.

I've tried ScummVM and YouTube and neither work. Looking at other posts, I've added the below to my usercfg.txt, from reading other threads they seemed to help some people. 

```
hdmi_force_hotplug=1
config_hdmi_boost=4
``` 

But still no joy. 

I have the following in my config.txt by default

```
param=audio=on
hdmi_drive=2
```

Any help would be appreciated. I have sound working on RetroPie and Raspian.

Edit: I should say, the monitor I am using is a Samsung 22 inch.

---

### Post by cmcanulty on 2020-08-08
This may not apply to you but I had the same issue and had to unplug the old mini jack sound cable and then presto had sound over HDMI

---

### Post by adambegood on 2020-08-10
[FONT=ubuntu]There is a section of Sounds Preferences called Output, where you can select two identical looking "Built-in Audio Stereo" options.

[/FONT]
[FONT=ubuntu]One has Connector set to "Analog Output", the other has "Headphones" - selecting "Analog Output" fixed the HDMI issue.

I cannot work out how to save it though, so it needs to be done each time I log on. Not a big problem though.[/FONT]

---

### Post by kolinab on 2020-08-17
You have probably already checked this since you have sound working on Retropi and Raspbian, but in my experience I had to plug the micro HDMI connector to HDMI 0 for sound, not HDMI 1 (HDMI 0 is the one closer to the power connector).

---

