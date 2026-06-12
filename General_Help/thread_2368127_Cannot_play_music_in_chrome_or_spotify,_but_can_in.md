---
title: "Cannot play music in chrome or spotify, but can in firefox"
date: 2017-08-07
forum: General Help
---

### Post by misenooooo on 2017-08-07
I am having lately issue with listening to music on my Ubuntu 16.04.

My chrome stopped playing music a couple of weeks ago.

Today I had to present my project and connected HDMI cable. I had my spotify muted, but it started to play immediaty after I plugin in the HDMI. So I muted it. After I finished my presentation I just unplugged the cable. Now I cannot listen to spotify music. 

I tried:

sudo pm-suspend 
sudo killall pulseaudio
sudo apt-get update
sudo apt-get install --reinstall pulseaudio
sudo service lightdm restart

and

pulseaudio -k && sudo alsa force-reload

Nothing works. In settings -> sound everything is set up correctly. I have no idea what is wrong.

I run $ aplay -l and this is my output:

**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: Generic Analog [Generic Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


I think something got stuck somewhere, but I cannot find the problem.

---

### Post by #&amp;thj^% on 2017-08-07
Do you have this (pavucontrol) installed?
To check:
```
apt policy pavucontrol
```
If not install it...it has better control for switching devices.
```
sudo apt install  pavucontrol 
```
Also I just use this to kill and restart pulseaudio:
```
pulseaudio -k
```
If it gets stuck...and if needed run this:
```
pulseaudio --start
```
Important to check that the right Device is used for the application like Browsers Music players etc etc.

---

### Post by misenooooo on 2017-08-07
Thank you for answer.

I have and it did not help. Where can I check the last one? I am almost sure spotify is trying to play the music on the hdmi device, which was disconnected and chrome somewhere else as well. Do you know how to reset this settings?

---

### Post by #&amp;thj^% on 2017-08-07
You will need to show me with pusleaudio volume control.
Example here: 2 Screenshots for mine, first shows my browser using my bluetooth headdset
Notice the tabs above in the window first showing "Playback" My browser firefox using the headset.
Second one shows the" Configuration Tab" with the enabled Devices to use.
EDIT 3rd added with Audacious playing through my builtin sound card.

---

### Post by misenooooo on 2017-08-07
When I run pulseaudio I get this.
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.
--kill and --start did not help

Can I ask you what do you see after you run alsamixer?

---

### Post by #&amp;thj^% on 2017-08-07
> **misenooooo said:**
> When I run pulseaudio I get this.
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.
--kill and --start did not help

Can I ask you what do you see after you run alsamixer?

I think you are misunderstanding me.:)
First Go to your menu>>>Now to Multimedia>>>then click on PulseAudio Volume Control to see those options I have shown.
Or open your terminal and run this:
```
pavucontrol
```
But it would be better just to open it through the menu though.
Alsamixer is not helpful here.

---

### Post by misenooooo on 2017-08-07
Thank you very much! Here was the problem. It was set to HDMI device. :) Thank you very much. :popcorn:

---

### Post by #&amp;thj^% on 2017-08-07
Cool! Glad we got to the solution.
Cheers :D

---

