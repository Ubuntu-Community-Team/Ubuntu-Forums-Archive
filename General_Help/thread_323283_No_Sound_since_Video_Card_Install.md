---
title: "No Sound since Video Card Install"
date: 2006-12-21
forum: General Help
---

### Post by mickbw on 2006-12-21
Hi,

When I installed Ubuntu Edgy I was able to listen to music through the onboard audio of my board.  

Since I installed my GeForce video card (which was successful) I no longer can hear  music in my linux install.  

If I go to system| preferences | sound , I can hear a test  pulse if I test the output but still no music. 

When I run XP I hear the audio without a problem.  Any help would be greatly appreciated.

Michael

---

### Post by shanepardue on 2006-12-22
Could it be a codec issue? Maybe you could try reinstalling the codecs needed for the music you're wanting to play. Does the initial ubuntu sound play when you log in?

---

### Post by mickbw on 2006-12-22
I am sure it is something very basic that I am just missing.  I did check and the onboard sound is still selected for use.  

No, I don't hear the default sound upon login either.  

Thanks for your reply.

---

### Post by tommcd on 2006-12-22
Try working your way through this:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
Hope it helps.

---

### Post by mickbw on 2006-12-22
I will do that tonight and post my results.  

Thanks for the link,

Michael

---

### Post by mickbw on 2006-12-22
Thanks, tommcd

I now have sound.  It was changing the values in alsamixer that resolved the problem.  I'm not sure what PCM is, but that was shut off.  Once I changed that value, I was able to hear audio.  

Thanks for all the help and Happy Holidays to all.

Michael

---

### Post by tommcd on 2006-12-23
Glad you got it going. On my system PCM seems to control the volume of the multimedia program i currently have running. For example, I have the master volume set to 100%, but if I listen to music with xmms or rhythmbox, or watch a video with vlc or totem, PCM will control the volume of those programs independent of the master volume setting. So having PCM shut off will mute the volume of the music player program you are using.

---

### Post by mickbw on 2006-12-23
That certainly makes sense then since I was trying to listen to Amorack.  

Merry Christmas to all.

---

