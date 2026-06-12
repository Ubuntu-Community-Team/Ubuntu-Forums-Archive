---
title: "Rhythmbox uses almost 100% CPU in Gutsy"
date: 2007-11-13
forum: General Help
---

### Post by rrwo on 2007-11-13
I've upgraded to Gutsy, and now when I listen to music in Rhythmbox, after a while it starts using nearly 100% CPU. Although it doesn't (always) seem to affect other applications running, it does affect the sound quality of the audio when it's playing.  Playback starts skipping.

Does anybody else have this problem?

---

### Post by bingoUV on 2007-11-13
Do you "watch" your music library for changes? Is this option checked?
Edit -> Preferences -> Library -> Watch my library for new files

---

### Post by rrwo on 2007-11-15
No, that doesn't fix the problem.

---

### Post by ericesque on 2007-11-15
Are you using emerald?  I had the same problem when I was running emerald and Rhythmbox.  I got rid of emerald and got rid of the issue at the same time :)

---

### Post by rrwo on 2007-11-19
No, I'm not using emerald or compiz.

I am using Xfce instead of Gnome.

---

### Post by rrwo on 2007-12-09
I found I had both Xine and Gstreamer libraries installed. I removed one of them, and the problem sems to have gone away. So maybe that was the cause....

---

