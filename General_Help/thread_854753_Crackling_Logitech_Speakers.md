---
title: "Crackling Logitech Speakers"
date: 2008-07-09
forum: General Help
---

### Post by Enkaybee on 2008-07-09
I think this could be a quick fix.  I have logitech speakers and they crackle whenever I try to play any audio.  The crackling increases with increased CPU usage.  I've changed the audio output frequency to 44100 Hz and got nothing (I then changed it back to 48000).  

What I'd like is for someone with similar speakers (non-crackling, of course) to post the full contents of his/her .asoundrc file so that I can copy/paste it into mine.  I'll change what I need to to make it play.

If not, any suggestions for a fix will be appreciated.

---

### Post by Activist on 2008-07-09
in terminal, type
> alsamixer

move the PCM to gain 0.

but i dont think this can be helpful :P , anyway

---

