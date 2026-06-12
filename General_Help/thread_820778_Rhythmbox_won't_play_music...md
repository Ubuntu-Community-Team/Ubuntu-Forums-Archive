---
title: "Rhythmbox won't play music.."
date: 2008-06-06
forum: General Help
---

### Post by Kromgol on 2008-06-06
Hello all,

Whenever i try to play music with rhythmbox, it never starts, it shows the title of the song and all that, but it never starts playing the music! Tried reinstalling, download the source code to the newest rhythmbox and compile etc. but nothing worked!
Nothing shows up in the terminal either.

Would be happy if anyone could help.

---

### Post by T_W on 2008-06-07
It may be a PulseAudio issue.  Do you have firefox running? Is the Flash plugin installed.  Flash and Pulse Audio have some major issues with both trying to own the sound stack.  Try shutting down firefox completely and trying again.

---

### Post by Sinkingships7 on 2008-06-07
Try this:
```
sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
```

---

### Post by Kromgol on 2008-06-08
That worked! Thank you :D

---

### Post by gandalf458 on 2008-07-19
Thanks - just what I needed too.

---

### Post by Kila_Bite on 2008-07-30
Hey guys, I tried the above fix and closed firefox and I'm still having this issue. I've tried two seperate music players, both Rhythmbox and Amarok (which confused me). I had problems with pulse audio in firefox before where it woulden't play the sound in flash videos such as youtube. That problem is now resolved however since then, no music from my players.

Edit: Ummm okay, nothing plays be it music or video. It just sits there when I open the file and won't play. If I move the bar slider forward I can skip through the song/video but they just won't play by themselves. Tried pausing/unpausing but as I'm relatively new to Ubuntu, I can't troubleshoot further than that.

---

### Post by shimi on 2008-08-04
This might help you to solve your [audio and video problem]("http://mylinuxnotebook.blogspot.com/2008/07/ubuntu-sound-flash-problem.html").

---

### Post by sircolin on 2012-09-29
Thanks

---

