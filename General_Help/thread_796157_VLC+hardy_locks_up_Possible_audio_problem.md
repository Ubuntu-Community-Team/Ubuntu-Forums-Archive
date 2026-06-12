---
title: "VLC+hardy locks up? Possible audio problem"
date: 2008-05-16
forum: General Help
---

### Post by dracovich on 2008-05-16
This is a problem i never had with 7.10, but i updated to Hardy now and although it had happened once or twice before in the past month, it's now happening quite frequently. Basically what happens is that i'll start playing a video file in VLC, and the screen will lock up. My mouse is still active, but i can't click anything, the keyboard is completely dead (i've tried restarting X using keyboard, didn't work). The sound from the video plays on but no video obviously, since the screen is dead. Only solution AFAIK is to shut down and reboot.

This isn't entirely a VLC problem though, i had the same thing happen to me two days ago when playing a video file in firefox (using mplayer), not sure of the format there, but it's almost always avi files in vlc that freeze.

At first i thought it was a problem with pulse-audio, it's been causing me problems on other fronts (i have to kill it in order to be able to play mp3's), and at one point i had frozen up 3x in a row in VLC, then i thought of killing pulseaudio and it worked, but i have since had it happen even if it wasn't running.

Any suggestions are well appreciated, this is incredibly annoying.

---

### Post by dracovich on 2008-05-17
Noone? It's happening quite frequently now, honestly starting to be a huge hassle.

---

### Post by dracovich on 2008-05-17
I should add that

1) It's not a VLC specific problem, the same happens when i try to play with mplayer

2) Doesn't appear to be a problem with pulseaudio, as i've had the same problem after killing it, and after going into preferences-sound and change it to ALSA.

Other then that i have no idea what is going on and googling about it hasn't helped at all.

---

### Post by enchantedsky on 2008-05-19
I have a similar problem as you.......for me, MPlayer locks up. Other video programs work though.

However, for me, I believe it is a Pulseaudio error because my System Monitor log says: "May 19 21:02:52 pulseaudio[5756]: protocol-native.c: Failed to push data into queue" whenever there is a lockup in the video program

Check your System ---> Admin -----> System Log to see what exactly is locking up your system.

As a not-so-good solution, I'm going to reinstall Ubuntu perhaps next week....and see if things get better.

---

### Post by pangloss on 2008-05-20
I'm experiencing the exact same symptoms: play a video in vlc or totem and complete lockup, but the audio keeps playing and I can move the mouse.

Same videos played fine in Feisty. I've had this happen regularly (but not every time) on both clean installs of 32bit and 64bit Hardy.

---

### Post by RSingh on 2008-05-29
I am having the same problem. I am typing this from my desktop while in the other room my laptop is frozen.

Play a video and the screen locks up. I can move the mouse and thats it.

](*,)

---

### Post by Beto on 2008-06-28
Same problem here!!! as some people have pointed out, it is not VLC related, as it happens with other players, it is not avi specifically related either as also happens to me when I try to watch a WMV file (don't blame Micro$ for this).

Does anyone have a solution, I really think it is audio related, because when I restart the computer, sometimes the audio is muted. If I try to watch the same video inmediatly after reboot, the video plays ok.

---

### Post by Scott Walker on 2008-07-13
Same problem here. Random lock ups on video playback. Sound keeps playing, mouse still works but everything else stays frozen. I have noticed that videos tend to work if I start them shortly after reboot. 

Hardware

Dell E1405
intel 945gma

---

