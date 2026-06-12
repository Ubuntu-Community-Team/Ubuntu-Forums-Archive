---
title: "Middle mouse button mutes sound regardless of context"
date: 2014-11-25
forum: General Help
---

### Post by stelarcf on 2014-11-25
Hello.

I'm running Ubuntu 14.04 LTS


Earlier today I updated after I was prompted. The next time I started the computer, my middle mouse button does nothing but mute/unmute the sound.


My mouse is a SilverCrest STMS 2219 A1

---

### Post by CantankRus on 2014-11-25
Is this also the case in the guest account?

---

### Post by stelarcf on 2014-11-26
I have tested it and indeed it is.

---

### Post by CantankRus on 2014-11-26
The sound is supposed to mute when you middle click on the panel sound icon.
You can also test if your middle click behaviour is due to compiz/unity by installing **gnome-session-flashback**
```
sudo apt-get install gnome-session-flashback
```
and logging in to the flashback Metacity session and testing.

---

