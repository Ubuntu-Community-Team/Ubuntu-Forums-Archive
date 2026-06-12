---
title: "the one thing ubuntu cant do: mute flash"
date: 2008-01-05
forum: General Help
---

### Post by KhaosMind on 2008-01-05
hi. I have a problem, i cant mute firefox or flash apps, in windows there is an aplication named flashmute who can mute the whole browser or flash, but i was unable to find anything like it for ubuntu, the point is that i dont want a firefox extension that blocks flash(flashblock:lolflag:) i want to stop sound from playing while i can still see the flash. So if there are any ways to do this you would win my eternal thanks, while i was searching i found this post, it doesnt resolve my problem but could be usefull
[http://ubuntuforums.org/showthread.php?t=49736](http://ubuntuforums.org/showthread.php?t=49736)
thanks for reading and sorry for my english

---

### Post by Shay Stephens on 2008-01-05
Well I don't have a direct answer, but I can tell you what I do.  I changed the keyboard shortcut for mute to Ctrl + End.  I can toggle mute on and off now with a simple one handed operation.  It is second nature now.  I also made Ctrl up arrow volume up and Ctrl down arrow volume down.  The "windows" key on the left of the keyboard handles the play/pause toggle for movies and rhythmbox and such too.

To change you keyboard shortcuts go to System, Preferences, Keyboard Shortcuts.

---

### Post by KhaosMind on 2008-01-05
thanks but, it is not what i was looking for( offtopic: is there anyway to make a keyboard shorcut for more than 1 volume control?)
from time to time i want to play flash games who doesnt have the mute sound option and listen music, or surf the web and listen to music without annoying ads speaking
but thanks anyway:)

---

### Post by zdux0012 on 2008-03-21
This annoys me also, I suspect it is possible to use a security setting to fix it.
perhaps something with /dev/dsp

---

### Post by KhaosMind on 2008-03-30
> **zdux0012 said:**
> This annoys me also, I suspect it is possible to use a security setting to fix it.
perhaps something with /dev/dsp
thanks someone feels the same, do you know how to fix it?

---

### Post by monraaf on 2008-03-30
I don't know about Gutsy but in Hardy you can set and mute the volume of individual applications, including Adobe Flash, with the PulseAudio Volume Control program.

---

### Post by KhaosMind on 2008-03-31
thanks a lot for the info. but i dont know if i will be able to use hardy because my ati radeon card is bad detected in the beta [http://ubuntuforums.org/showthread.php?t=739325]("http://ubuntuforums.org/showthread.php?t=739325")

---

### Post by KhaosMind on 2008-04-02
i been trying to use pulseaudio volume control but i dont understand how to mute flash. could you explain it? 

> I don't know about Gutsy but in Hardy you can set and mute the volume of individual applications, including Adobe Flash, with the PulseAudio Volume Control program.

---

### Post by monraaf on 2008-04-02
Go to YouTube play a video and Adobe Flash will show op in the PulseAudio Volume Control (see attachment), then just click the speaker icon.

Just to be sure we are talking about the same application, it's called **pavucontrol**, and it's not installed by default in Hardy.

Also, you must make sure that all your applications are using pulseaudio as ouptut. For alsa: **asoundconf set-pulseaudio**

---

### Post by gardara on 2008-06-12
> **monraaf said:**
> Go to YouTube play a video and Adobe Flash will show op in the PulseAudio Volume Control (see attachment), then just click the speaker icon.

Just to be sure we are talking about the same application, it's called **pavucontrol**, and it's not installed by default in Hardy.

Also, you must make sure that all your applications are using pulseaudio as ouptut. For alsa: **asoundconf set-pulseaudio**

Awesome! I tried this and it works!
But well first I had to enable flash support for PulseAudio, followed this manual and got it all working. [http://www.pulseaudio.org/wiki/FlashPlayer9Solution](http://www.pulseaudio.org/wiki/FlashPlayer9Solution)

---

