---
title: "Fresh Install NO sound :("
date: 2008-06-01
forum: General Help
---

### Post by Lateralus561 on 2008-06-01
Hi guys, I'm attempting to make the transition from XP to Ubuntu. I consider myself somewhat tech savvy, but am brand new to Ubuntu. Everything is working great, except for my sound. I heard the start up drum sound, but nothing else will make a noise. I've tried tinkering with the volume control, and all of the different device selections, but still to no avail. I've also tried looking under the hardware section, making sure my volume was muted or low... etc..    Please help!

---

### Post by goldust on 2008-06-01
I always have had trouble with sound in ubuntu and other distributions and it's almost always usually solved by seeing how the sound reacts when I turn off and turn on switches in the Switches tab in volume control.

Also check out sound preferences and see what device is selected in default mixer track, and play around with the various choices for sound playback. I've found that ALSA works best for me.

---

### Post by kureyamu on 2008-06-02
hi

you should be able to set up your sound in System/Preferences/Sound/Devices

there are drop down menus for Sound Events, Music and Movies, Audio Conferencing ... each one should show the sound system that works ... test each element in the drop down menu with your speakers ... one of them should beep like billyho ... so make this selection eg ALSA the same for all of the three categories

and if your selected system is different from ESD which is selected in System/Preferences/Sound/Sounds, you may have to untick that box (i had to) and then the sound worked perfectly ... i think ESD was turning off the volume control used by the other system at boot

if setting selections in System/Preferences/Sound does not work for you, open a terminal and view your sound cards with the command line:

cat /proc/asound/modules

if you see, for example, 3 soundcards called:

0 snd_via82xx
1 snd_ens1371
2 snd_mpu401

you can set the order of priority (your first priority is like a default) for example BAC with the following, leaving a space between each group of words and only pressing Enter when you have typed the whole lot:

sudo  nano  /etc/modprobe.d/alsa-base
options snd-B index=0  options snd-A index=1  options snd-C  index=2

you may have to play around a bit until you get the priority right, and then your sound should work.

after any changes and before testing by playing a CD track or whatever, remember to reboot so that the changes can take place

regards

kureyamu


*[CENTER]microsoft was a 20th century software company[/CENTER]*

---

