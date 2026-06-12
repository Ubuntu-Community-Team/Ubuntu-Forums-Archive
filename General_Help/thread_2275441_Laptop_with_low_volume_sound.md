---
title: "Laptop with low volume sound"
date: 2015-04-26
forum: General Help
---

### Post by andfree on 2015-04-26
The sound of my laptop is too low volume. I installed pulseaudio and pavucontrol via terminal, but I don't find pavucontrol at the menu.

---

### Post by pqwoerituytrueiwoq on 2015-04-26
try running it from a terminal
launcher is here
/usr/share/applications/pavucontrol.desktop

"PulseAudio Volume Control" should be in the menu under audio or video

---

### Post by andfree on 2015-04-26
There's not pavucontrol.desktop in /usr/share/applications. There's PulseAudio Volume Control (in /usr/share/applications and in the sound & video menu).

Increasing the %dB from Volume Control increases the volume, but with very bad quality.

---

### Post by mattharris4 on 2015-04-28
From my experience Lubuntu 14.04 does not use pavucontrol, it uses alsamixer instead.  Here are the instructions you need to get your sound working properly:

Read this link, step 2:  [http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/](http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/)

Here is the instructions in a nutshell:  
1.  Get into a terminal (Ctrl+Alt=T)
2.  Enter "alsamixer" without the quotes and press enter
3.  Enter your sudo password if requested
4.  Select your sound card using F6 
5.  At the bottom of the "Master", "Headphon", and "Speaker" there may be an MM or a low number.  Move your cursor with the left and right keys until it is under "Master".  If MM appears press "M" to unmute, the "M" will change to "00".  Then use the up arrow to turn the volume up to about 80, it will show as a yellow number under the line graph of whichever function you are dealing with (if you go too high use the down arrow to correct).  Do the same to "Headphon" and "Speaker" using the right arrow (or left if you overshoot) to move the cursor
6.  Exit Alsamixer with Esc. key
7.  Play sound file to test.

This is what I had to do to get sound on my Lubuntu 14.04 installation.  Good Luck!

---

