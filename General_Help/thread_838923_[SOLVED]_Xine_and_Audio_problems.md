---
title: "[SOLVED] Xine and Audio problems"
date: 2008-06-23
forum: General Help
---

### Post by abuakel on 2008-06-23
Well, this has been happening for a while now.
I'm running Ubuntu Hardy 8.04

For some reason, after a certain amount of time, the audio stops working. I can't hear my Pidgin sounds as well as my Amarok music.
When I hit play in Amarok, I'm given this error:
"Audio output unavailable; the device is busy.
xine parameters: "

However, when I play a video in firefox or listen to music in firefox, I have no problem.
As of now, the only fix I've come across is to log out and log back in or restart the computer.

Any suggestions?

---

### Post by abuakel on 2008-06-24
Nothing?

:bump:

---

### Post by jpeddicord on 2008-06-24
The problem is most likely Flash in your browser. Ubuntu runs a service known as PulseAudio which controls almost all audio on your system. Flash is a notable exception. Instead of plugging into PulseAudio, it tries to output sound directly to your speakers via ALSA. The problem with this? PulseAudio also wants to use ALSA, both of them try to lock the system at the same time. So, if Flash is using sound, PulseAudio can't, and vice-versa. If you need sound in other applications, simply close your web browser and sound should return.

---

### Post by abuakel on 2008-06-24
> **jacobmp92 said:**
> The problem is most likely Flash in your browser. Ubuntu runs a service known as PulseAudio which controls almost all audio on your system. Flash is a notable exception. Instead of plugging into PulseAudio, it tries to output sound directly to your speakers via ALSA. The problem with this? PulseAudio also wants to use ALSA, both of them try to lock the system at the same time. So, if Flash is using sound, PulseAudio can't, and vice-versa. If you need sound in other applications, simply close your web browser and sound should return.

Thanks for the reply.
I tried what you said with no luck.
I've also noticed that after I lose sound, I'm introduced with a whole world of problems such as amarok not loading, and greying out. When I try to pull up the terminal to kill amarok, it greys out as well. then, firefox won't open again. I can't log out, so I end up logging out by hitting <Ctrl> + <Alt> + <Backspace>
Previously, when I signed in after I hit <Ctrl> + <Alt> + <Backspace>, it would work fine.. but recently, I get a half white, half ubuntu-colored screen with a txt cursor. 


ahh, I've never had this many problems with Ubuntu :confused::confused:
although highly unlikely, I'm starting to think I've got a virus?? even though I know it's nearly impossible to get one

---

### Post by jpeddicord on 2008-06-25
I've had this problem once, though it was during the alpha phase. What it seems to be doing is freezing PulseAudio. If apps that use sound start to freeze like that, hit Alt+F2 and type **killall pulseaudio**. Those apps will either then crash themselves or stay frozen, so you should probably close them as well. Then, hit Alt+F2 again and simply type **pulseaudio** to restart the sound server. Try your audio applications again and see if it helps.

---

### Post by abuakel on 2008-06-25
> **jacobmp92 said:**
> I've had this problem once, though it was during the alpha phase. What it seems to be doing is freezing PulseAudio. If apps that use sound start to freeze like that, hit Alt+F2 and type **killall pulseaudio**. Those apps will either then crash themselves or stay frozen, so you should probably close them as well. Then, hit Alt+F2 again and simply type **pulseaudio** to restart the sound server. Try your audio applications again and see if it helps.

Worked like a charm.. thanks. :D

---

### Post by bembou on 2008-11-12
thank you very much

---

