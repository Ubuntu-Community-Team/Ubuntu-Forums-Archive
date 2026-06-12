---
title: "Sound stopped working on some programs"
date: 2006-11-17
forum: General Help
---

### Post by Sunborn on 2006-11-17
Ok, I got dapper drake 6.06.1 on my ibm R60 thinkpad. Sound was working fine. I got my hands on one of my favourite games in the world, Alpha Centauri. After installation, I kept getting a segmentation fault and thought it was this bug: [http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games](http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games). So I installed the backup .so's and used 
```

LD_LIBRARY_PATH=/path/Loki_Compat/ /path/Loki_Compat/ld-linux.so.2 /path/AlphaCentauri/smacx.dynamic 

```
to run the game, only to find out that it was the permissions on the temp directory stopping it from running. 

After this, the sound in Quake 3 Arena and Firefox stopped working. Sound WORKS in Rhythmbox, Gaim and the opening sound on ubuntu. Killall -9 esd didn't work. The sound is not muted, I checked with alsamixer. Gstreamer seems to work, and so does esd. I don't know what FF and Quake has in common. Most interestingly, Alpha Centauri's sound did work, but now doesn't after the first restart after installation at the same time the sound stopped working.

No idea what is going on, the only thing I did out of the ordinary is above.

---

### Post by Sunborn on 2006-11-17
Ok, development, sound in alpha centauri works if I do actually use the ```
LD_LIBRARY_PATH=/usr/local/Loki_Compat/ /usr/local/Loki_Compat/ld-linux.so.2 /usr/local/games/smac/smacx.dynamic

```

So what did I do to stop Quake 3's sound and Firefox to loose sound? How do I get this sound back?

---

### Post by Sunborn on 2006-11-17
It turns out the sound was failing for all the programs independantly. This was not a common-mode failure. SMAC's sound failed because the librarys had to be forced, Quake 3 because Rhythmbox was open, and Firefox because of the common flash sound stop working bug.

[http://www.macewan.org/2006/06/01/howto-firefox-flash-video-sound-on-ubuntu-linux-dapper/](http://www.macewan.org/2006/06/01/howto-firefox-flash-video-sound-on-ubuntu-linux-dapper/)

Thanks though to all that read this for the potential help. This thread can be closed.

---

### Post by strabes on 2006-11-17
you can also put 'aoss' in front of a command for a program that uses sound to prevent it from monopolizing your sound card. example: ```
aoss firefox
```

---

