---
title: "Sound problems - Can't have sound at two programs at the same time"
date: 2016-07-25
forum: General Help
---

### Post by markodd on 2016-07-25
Hello,


Something weird is going on with my Ubuntu system. I recently installed Ubuntu 16.04 and I'm having all kinds of problems, it was definitely a bad idea to install it. 

Right now, the problem is the following:

Sound doesn't work when I've two programs that require it at the same time. For example, if I open youtube only, I'm able to hear a video. However, If I also have a movie opened, I won't be able to hear the movie nor youtube.

Anyone knows what's going on?

---

### Post by yoshii on 2016-07-25
Check to see if the programs are using ALSA or JACK instead of PulseAudio.  PulseAudio can share the audio hardware amongst various simultaneous programs, but JACK usually can't without special help.  I think the same is true for plain ALSA.  Also, if you are using anything ASIO, that is always done with "exclusiveness" so that only one program has audio at a time.  For Wine programs, use PulseAudio for Wine, and then in the program try selecting WASAPI (if it's a Windows program) and set the mode to "shared".  Good luck.

---

### Post by Yellow Pasque on 2016-07-26
Make sure pulseaudio is running. I know sometimes I have to manually start it on my Ubuntu Mate VM for some reason (probably a bug that I haven't had the inclination to look into):
```
pulseaudio -D&
```

---

### Post by markodd on 2016-07-29
Hey, thank you for the answers.

I found the problem to be firejail. For posterity sake, I solved the problem by doing what is suggested in the following page:

[https://firejail.wordpress.com/support/known-problems/#pulseaudio](https://firejail.wordpress.com/support/known-problems/#pulseaudio)

---

