---
title: "Nautilus shrinks when opening folders"
date: 2006-10-27
forum: General Help
---

### Post by Ferio on 2006-10-27
Since I upgraded yesterday to Edgy, Nautilus shrinks its size when I open a folder. I mean, if it's maximized, then it turns into a small window in the center of the screen, showing only 3 columns x 2 rows of icons.
Any idea?

---

### Post by bsussman on 2006-10-27
try increasing the size to that which you like and then File -> Close

After that try opening again.  Is it as big as you want?

Nautilus attempts to save state in many cases.  This might explain the behavior you see.

---

### Post by Ferio on 2006-10-27
No, it keeps on its odd behaviour; what's really strange about it is that now it seems to do it at ramdom: sometimes Nautilus goes on with the same size, sometimes shrinks itself, and sometimes goes back to maximized. Not really a problem right now, but an annoying behaviour :???:

---

### Post by bsussman on 2006-10-27
that is strange - if I was sitting at your screen I might be able to figure it out but barring that, I haven't a clue ](*,)

---

### Post by Ferio on 2006-10-28
I've just found that it's saving its state, but only for the folder  that it's browsing when I close it. Example: I open my home folder, and it's maximized; then, I open A, that it's in home, and because of it Nautilus becomes a tiny window; I maximize it, and then close Nautilus. Next time I use it to browse into A, it will stay maximized, but if I browse into another folder that hasn't been maximized and immediately closed formerly, it will shrink again.

---

### Post by bsussman on 2006-10-28
I am not a nautilus expert, but there may be a way to keep it from remembering geometry.

Maybe somebody else will wander by with an answer.

---

### Post by gbutler69 on 2006-10-28
You've activated "Spatial" mode. That is a good thing IMHO. By default, Ubuntu turns off "Spatial" mode, you must've somehow got it turned on. To turn "Spatial Mode" back OFF, use the 'GConf Configuration Editor" (you can install it from Synaptic if you don't already have it). Then Changing the following setting:

   apps/nautilus/preferences/no_ubuntu_spatial

I prefer the setting "OFF" which seems to give me proper spatial mode. You may want it "ON" (or "OFF") -- hard to tell from your description. But, I think one option or the other will be what you prefer. Also, you may want to take some time to understand "Spatial Mode". Me, I much prefer it (once I got used to it)!

Just Google for "gnome nautilus spatial mode". There're are plenty of links explaining the whye and wherefore.

Hope this helps! Have Fun! :)

---

### Post by Ferio on 2006-10-28
Well, I'm sure this would help me, but I have not this option in my GConf Configuration Editor! This is becoming weird... :???:

---

