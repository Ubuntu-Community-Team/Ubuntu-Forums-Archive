---
title: "Rhythmbox/Amarok/Totem not playing when Play is pressed"
date: 2008-05-08
forum: General Help
---

### Post by wickerchick on 2008-05-08
Hello all,
I just upgraded to Hardy, and lately this strange problem occurs, seemingly at random.  At times, if I load up Rhythmbox, it will function normally, but if I close it and and open it again, or use either Amarok or Totem, and try to play something, nothing gets played.  What I mean is, I'll press play, it says it's "Playing"m but no sound will come, the duration bar is still stuck at 0:00 (and no, it's not under the "Paused" status:P).

This does not happen with Audacious, so it's possibly Gstreamer related, but I'm not sure.

Does anyone know what the cause of this can be?  Any insight can help!  Thanks!

---

### Post by lstarba on 2008-05-22
Hi, I've encountered the very same problem on my system. It's pulseaudio related. I don't know how to fix it to work properly yet though I'll investigate it further.

But for now, I can give you a hint on some walkaround. Go to System -> Preferences -> Sound and choose ALSA for your default sound source.

If you're not sure, if ALSA is configured properly try mpg123 and alsamixer.

---

### Post by noland on 2008-06-01
Same here.  Actually Totem plays the movies, but at about one frame every 2 seconds, and no sound is played in either application.  In my case the only way to fix it when it happens is "windows" based........... reboot!!!  This is kinda annoying, but seems to be one of the issues of Hardy... and i dont have a clue on how to find out what the problem is...  oh well we will see!

All right i went in the "System, Preferences, Sound" and it is in my case already set to use the ALSA mixer.  When i run all the tests, no sound comes out and its as if the computer does not find anything wrong.  Are there any ways to see the results of those tests?  Also since i upgrade to hardy, sometimes when i put my computer in hibernation, the screen will go either blue or white, and  a loud high pitch beep is heard for about 2 seconds.

---

### Post by nailzilla on 2008-06-02
After booting to xp then rebooting to ubuntu hardy I experienced the same issue.  My music is stored on my external HD and it was all viewable, not an issue with mounting.  When I pressed play it would push the button and my external HD would get activity, but it would stick at 0:00s.

System -> Preferences -> Sound showed that my Sound Events playback was set to Automatic, as was my Music/Video playback.

I changed these both to my soundcard type: "ALC880 Analog" and everything is back to normal.

---

### Post by noland on 2008-06-05
All right in "system, preference, sound" i changed the "Music and Movies" section in the "devices" tab to "ALC861VD Analog" instead of "autodetect" which i guess is the internal soundcard or i dont know?  anyways it works... Its weird thought that the "autodetect" does not autodetect... thx everyone ;)

---

### Post by mhedges48 on 2008-07-10
changing it to ALSA as directed above fixed mine (I was having the same problem); thanks!!! Pulse seems to be problematic for me (doesn't work when I test it).

---

### Post by Vryko Lakas on 2008-07-11
lstarba's workaround also fixed the issue for me. 
I was having the same problem as wickerchick with Rhythmbox just now. I don't know if it was some update, trying out a non-repository version of Exaile, or listening to pandora.com streams that caused pulseaudio to hang for me.

---

### Post by Nicolas Raoul on 2008-09-07
I had the same problem on Ubuntu Hardy Heron 8.04.1:

Rhytmbox does not play any sound when I click "Play", the time cursor stays stucked on 0.
Amarok does not play any sound. For the first few seconds, the time cursor first moves and the visualizer dances on frequencies, but then it stops. Double-clicking on another song during those few seconds results in Amarok freezing.
I was working fine last week, so I am wondering what happened. I do not have any other operating system, so it is an Ubuntu issue.

I fixed it this way:

Close Rhythmbox and Amarok
Go to System > Preferences > Sound
Change the 3 "Sound playback" settings from "Autodetect" to "ALC260 Analog" or what looks similar in your particular case.
Close
Launch Rhythmbox again: it now plays sound correctly.

But the problem with Amarok is still here, it also crashes whenever I load a new song... probably a different bug

Cheers !
Nicolas.

---

### Post by Predator106 on 2008-09-07
I have the same problem, except for me (I believe this is related), only one application can use the sound device at a time. Thus, this meaning if I watch a youtube video or listen to Pandora through Firefox, and then want to switch to Banshee to listen to my own music, I have to close firefox(to mark the device as free) and then start up banshee (before firefox, so it can mark the device as used), in which case Firefox can't use it then...

---

### Post by mb_webguy on 2008-09-07
Try the "PulseAudio fixes in Hardy" link in my signature.  It worked for me...

---

### Post by Predator106 on 2008-09-09
Was that directed to me?

---

