---
title: "Rhythmbox Pauses/Delays"
date: 2005-08-04
forum: General Help
---

### Post by Gnuklear on 2005-08-04
Hello all,

I posted about something similar before, when I thought this was a much more general error (something possibly hardware related) however after some fairly extensive testing, I'm 99% sure it is unique to Rhythmbox.

The problem is that when I try to play FLAC encoded files, or even when I play MP3's and Vorbis files (though much less often), Rhythmbox will occasionarlly pause, and by that I mean that it will stop playing for about a second, as if it were buffering, and then start back up. I tested this in XMMS to see if it also occured there (meaning some deeper system issue) and was unable to replicate the problem. Then, thinking this might be a problem with GStreamer, I tried to recreate the error in Totem and again was unable to, meaning, as far as I can tell, that this is unique to Rhythmbox.

Is this an issue that someone is aware of and has a fix for, or should I be submitting a bug report?

---

### Post by charlieg on 2005-08-04
You could try reporting it to the [email]rhythmbox-devel@gnome.org[/email] list... I have noticed it (very rarely) happen to Rhythmbox on my machine too, but not enough as to be problematic.

---

### Post by Tamir on 2005-08-04
[QUOTE=charlieg]You could try reporting it to the [email]rhythmbox-devel@gnome.org[/email] list... I have noticed it (very rarely) happen to Rhythmbox on my machine too, but not enough as to be problematic.[/QUOTE]
 I have this too! I am amd64 user.

---

### Post by Gnuklear on 2005-08-04
[QUOTE=Tamir]I have this too! I am amd64 user.[/QUOTE]

Really? That's interesting... I'm on an AMD64 system, but I'm running the 32bit edition (as it's a bit more stable at the moment to my knowledge). I'll file an Ubuntu Bugzilla report first, then move upstream from there if necessary.

---

