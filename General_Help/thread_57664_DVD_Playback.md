---
title: "DVD Playback"
date: 2005-08-17
forum: General Help
---

### Post by lyam_kaskade on 2005-08-17
I've looked through the forums, and can't seem to find anyone with the same problem as mine. 
Whenever I try to play a DVD in Xine, it freezes. No errors, it just stops responding. The same thing happens in Totem and MPlayer. 

I've already downloaded libdvdcss2 and all of the multimedia codecs (as indicated in the ubuntuguide). 
If anyone could shed some light on this problem, it would be greatly appreciated.

---

### Post by ssck on 2005-08-17
[QUOTE=lyam_kaskade]I've looked through the forums, and can't seem to find anyone with the same problem as mine. 
Whenever I try to play a DVD in Xine, it freezes. No errors, it just stops responding. The same thing happens in Totem and MPlayer. 

I've already downloaded libdvdcss2 and all of the multimedia codecs (as indicated in the ubuntuguide). 
If anyone could shed some light on this problem, it would be greatly appreciated.[/QUOTE]

i have the exact same problem but have not been able to solve it ....  ](*,) 

it just freezes .....  ](*,)

---

### Post by mcmuffy on 2005-08-17
Is it with all discs or just specific ones? I have a problem with xine (and other players) crashing with disc 1 of the stargate season 7 box set although the disc works fine in windows. All others work fine though.

---

### Post by lyam_kaskade on 2005-08-17
[QUOTE=mcmuffy]Is it with all discs or just specific ones? I have a problem with xine (and other players) crashing with disc 1 of the stargate season 7 box set although the disc works fine in windows. All others work fine though.[/QUOTE]

**checks about a half dozen dvds** 

Nope, it's definitely all discs.

---

### Post by ssck on 2005-08-17
[QUOTE=mcmuffy]Is it with all discs or just specific ones? I have a problem with xine (and other players) crashing with disc 1 of the stargate season 7 box set although the disc works fine in windows. All others work fine though.[/QUOTE]

it happens to all discs.but i find that if i use xfce using ogle, it can play longer although it still freezes with or without dma on.

 ](*,)

---

### Post by grj on 2005-08-17
Try installing totem-xine. I could not play dvds at all until I installed this.

---

### Post by lyam_kaskade on 2005-08-17
>  Try installing totem-xine. I could not play dvds at all until I installed this.

Yeah that was the first thing I tried. I also tried Kaffeine and VLC, got the same problem. Normal video files seem to work though.

---

### Post by henrrrik on 2005-08-17
totem-xine was causing problems for me (even caused Nautilus to crash when opening Properties by right-clicking on media files). 
totem-gstreamer (+ all the packages required for DVD-playback as listed on ubuntuguide.org) works fine though.

---

### Post by lyam_kaskade on 2005-08-18
Okay, I've managed to get DVDs to play (flawlessly too, as far as I can tell) by using the bash terminal to run MPlayer:

mplayer dvd://1
(and mplayer -h for a list of commands)

but when I use the GUI it still crashes everytime, forcing a reboot. Anyone have any idea what could be happening?

---

### Post by arnieboy on 2005-08-18
[QUOTE=lyam_kaskade]Okay, I've managed to get DVDs to play (flawlessly too, as far as I can tell) by using the bash terminal to run MPlayer:

mplayer dvd://1
(and mplayer -h for a list of commands)

but when I use the GUI it still crashes everytime, forcing a reboot. Anyone have any idea what could be happening?[/QUOTE]
go to preferences in mplayer gui and try setting the audio driver to OSS and the video driver to xv. let me know whether this works for u or not.

---

### Post by lyam_kaskade on 2005-08-18
The video driver was already set to xv,  but I switched the audio driver.
It still crashes, but this time it gives an error as well:

could not open/initialize audio device--> no sound

---

### Post by arnieboy on 2005-08-18
[QUOTE=lyam_kaskade]The video driver was already set to xv,  but I switched the audio driver.
It still crashes, but this time it gives an error as well:

could not open/initialize audio device--> no sound[/QUOTE]
do something. uninstall mplayer and follow my HowTo on:
[http://ubuntuforums.org/showthread.php?t=31061](http://ubuntuforums.org/showthread.php?t=31061)

---

### Post by lyam_kaskade on 2005-08-18
k, compiled it through source. 
I still get the same error as above, though it doesn't freeze anymore, it just closes. 
It also no longer works through the terminal. :(

---

