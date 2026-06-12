---
title: "Ubuntu Edgy hangs, mouse OK, sound OK"
date: 2007-04-16
forum: General Help
---

### Post by Arlanthir on 2007-04-16
This happens to me quite frequently:
Ubuntu Edgy hangs visually (nothing is refreshed but the mouse) while the sound continues playing. I can't do ANYTHING besides hard-rebooting the laptop (besides, well, moving the mouse to the sound of music).
I'm using Beryl from the repos (0.2.0~0beryl1).

Any thoughts? 
Thanks!

---

### Post by sirevert on 2007-04-16
Same problem for me, made a post on this forum earlier also:
[http://ubuntuforums.org/showthread.php?t=410786]("http://ubuntuforums.org/showthread.php?t=410786")

No errors in any log files.

---

### Post by Arlanthir on 2007-04-17
Thank you for the confirmation!
I couldn't find any similar post, but I guess I'm not the only one to post this happening ;)

---

### Post by Nachimir on 2007-04-17
This happens to me too occasionally, usually a very short time after logging in. Just like you, sound output continues, and the mouse pointer moves, but the desktop itself appears to be completely unresponsive. Keyboard shortcuts (such as CTRL + Alt + F2) also seem to be unresponsive.

Sometimes I can go for weeks without it happening though.

Are you both running Beryl or Compiz too? If so, that might easily have something to do with it.

---

### Post by SigmundFreud on 2007-04-17
It's Kwin that hangs (it's the program that draws the panel and windows and so on). You need to restart that, but I don't know how to do that from different console screen. I managed to do it because I have two screens. So I moved the mouse to my second screen/desktop, pressed alt-f2 and typed 'kwin', and that worked even better than restarting explorer.exe on Windows.

---

### Post by Arlanthir on 2007-04-17
I think it's impossible to restart on only one screen, because it's completely unresponsive and well, I can't change to the console mode that way. So, the safe way, how to prevent Kwin from hanging?? ;)
Thank you very much for the additional info!

EDIT: Now that I've searched about this, I don't have Kwin since I'm using gnome, so, it must be the gnome-equivalent of Kwin hanging for me. Is that metacity? If not, what is it?

---

