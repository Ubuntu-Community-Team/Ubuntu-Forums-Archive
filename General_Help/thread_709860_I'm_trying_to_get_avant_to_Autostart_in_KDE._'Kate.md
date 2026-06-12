---
title: "I'm trying to get avant to Autostart in KDE. 'Kate' is opening my script on startup"
date: 2008-02-27
forum: General Help
---

### Post by Biggus on 2008-02-27
Hi chaps.

I've got a rather spiffy little dock thingamajig called 'avant window navigator', and I've got it running splendidly in Gnome.

I've been attempting to get the blasted thing to execute in KDE also, upon login.

Now, what I've done is I've created a little 'script' in a folder called /home/.kde/Autostart and I've called it 'awnstartup'.

This is the content of my script :

```
#!/bin/bash
sleep 30 && avant-window-navigator
```

I've also changed the permisissions on it, using 'chmod 755'.

The dock itself starts up superbly, but I seem to have done something which is causing the rather unfortunate side effect of the program called 'Kate' (which appears to be a text editor of sorts) also opening up on startup, and it appears to be opening up the script which I use to start the avant-window-navigator dock.

I was just wondering if any technical boffins had any ideas as to what may be causing this behaviour, with regards to Kate opening up my startup script, on startup?

It's not a big problem by any means, but it is just annoying me that I don't know what's causing it.

Many thanks for any assistance which anyone could render unto myself.

---

