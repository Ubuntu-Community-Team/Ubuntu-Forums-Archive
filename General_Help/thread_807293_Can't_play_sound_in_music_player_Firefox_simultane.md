---
title: "Can't play sound in music player/ Firefox simultaneously"
date: 2008-05-25
forum: General Help
---

### Post by DavidCain on 2008-05-25
For some reason, I can't get sound output from a music player and Firefox simultaneously. Even if I pause the player or, say a flash video, in Firefox, it won't fix the problem. I've experimented with several music players (Banshee, Amarok, Kaffeine, and Rhythmbox). The problem is the same with all players. If I start up a player first, sounds won't work in Firefox. If I start up Firefox first, sounds won't play in the player. Does anyone know how I can fix this?

---

### Post by ownaginatious on 2008-05-25
I think this is a bug. The software sound mixer seems to be really screwed up in Ubuntu. One way you can get it to work is by killing the process "pulseaudio". After doing so, restart both firefox and amarok or w/e music player you are using, and both should be able to play simulataneously. This is a really annoying problem though; the solution doesn't seem to work for some applications like Unreal Tournament 2k4 where I want music and the game sounds at the same time...

Hope that helps!

---

### Post by DavidCain on 2008-05-25
I'll give it a try, thanks. I forgot to mention that this is a bug unique to Firefox. I can play WoW or other games with music in the background and it works just fine. Yea, I'm thinking of downgrading to Firefox 2.... Again.

---

### Post by ~Nightingale~ on 2008-05-26
same, but not just with firefox, all programs

---

### Post by thedevnull on 2008-05-26
Same here.

---

### Post by sgreddin on 2008-05-27
I had the same issue. I use Rhythmbox and flash wouldn't play at the same time as my player. Also, even after restarting both Firefox and Rhythmbox, Rhythmbox would simply not play. But i fixed it by going System> Prefernces> Sound, switched Sound Events, Music and Movies, and Audio Conferencing to PulseAudio Sound server. You may need to only swithc Music and Movies, but i ytypically go for overkill to make sure it works. Next, Alt+F2 and type "killall pulseaudio". At this point my computer slowed down, froze for a few moments, and then resumed. It still wouldn't play from Rhythmbox but i simply rextarted the computer, and now I have simultaneous audio and no freezing
Hope this helps!

---

### Post by Dizzy87 on 2008-06-01
Hey, I ran into the same problem i have 8.04 with youtube and movie player open at the same time. Instead of changing anything i found this : [http://www.paulbetts.org/projects/libflashsupport_1.0~2219-2_i386.deb]("http://www.paulbetts.org/projects/libflashsupport_1.0~2219-2_i386.deb")d

While installing it, it told me the file was out of date, but i installed it anyway and now i have the ability to have both my music player and youtube on firefox open at the same time.

---

### Post by Zorael on 2008-06-02
There's a version of that package (libflashsupport) in the repositories. Grab it through Synaptic or via apt/aptitude.
```
$ sudo aptitude install libflashsupport
```

---

### Post by marcosvega1 on 2008-09-16
Hi,

Thank you very much for this help, the package libflashsupport resolved this issue with firefox and media players.

:) Thanks again

---

### Post by willix on 2008-09-16
Did it for me too, thanks a lot
Would gladly have clicked the thanks icon, but your answer looks to have come before this new feature :-(

---

### Post by Nepherte on 2008-09-16
The issue mentioned here goes beyond flash sound problems. There's a bug in pulseaudio that, in general, denies access to every other app than the first one that tries to access the sound card. The rest of the applications is denied access. There are 2 possible solutions. The first one is just using alsa directly instead of pulseaudio (system > preferences > sound, change everything to alsa). The second solution involves fixing the bug in pulseaudio. There's a very simply straightforward copy/paste tutorial here (still no reason not to read everthing very carefully though): [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I leave it up to you what solution to pick. They should both work. The first one is a lot easier, but then again, you can do great things with pulseaudio if functioning correctly.

---

### Post by theMuffinMan on 2008-09-16
Zorael, my life is now complete.  Thank you so much.

---

### Post by davidryder on 2008-09-23
> **sgreddin said:**
> I had the same issue. I use Rhythmbox and flash wouldn't play at the same time as my player. Also, even after restarting both Firefox and Rhythmbox, Rhythmbox would simply not play. But i fixed it by going System> Prefernces> Sound, switched Sound Events, Music and Movies, and Audio Conferencing to PulseAudio Sound server. You may need to only swithc Music and Movies, but i ytypically go for overkill to make sure it works. Next, Alt+F2 and type "killall pulseaudio". At this point my computer slowed down, froze for a few moments, and then resumed. It still wouldn't play from Rhythmbox but i simply rextarted the computer, and now I have simultaneous audio and no freezing
Hope this helps!

Thanks! You should repost this so we can all thank you!!! You don't understand how frustrating this was.... :guitar:

---

### Post by labou on 2008-11-08
> **Zorael said:**
> There's a version of that package (libflashsupport) in the repositories. Grab it through Synaptic or via apt/aptitude.
```
$ sudo aptitude install libflashsupport
```

Thanks, this worked for me also.

---

