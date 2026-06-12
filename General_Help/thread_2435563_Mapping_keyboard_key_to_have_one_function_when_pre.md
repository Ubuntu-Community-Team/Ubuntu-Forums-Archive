---
title: "Mapping keyboard key to have one function when pressed and another when held"
date: 2020-01-22
forum: General Help
---

### Post by bobrocks on 2020-01-22
I have been using a mac a lot lately and got in the habit of having CAPS LOCK remapped to escape if you press it quickly and CONTROL if you hold it.  
On macos this was easy but as I switch back to linux I want to keep the same behaviour if possible.  I couldn't find any solution to configure this setup though, changing CAPS LOCK to escape was easy but the multiple functionality not so much.

Is it possible to do this in X?

---

### Post by dragonfly41 on 2020-01-22
I use AutoKey for running hot key python scripts. Possibly you might write a script in AutoKey which acts on CAPS LOCK key pressed,  scans the key for a time period and calls different functions if key is (a) released (b) held down.

---

### Post by bobrocks on 2020-02-13
Sorry I got stuck in mac world for a bit there.  I was just looking through the docs for autokey and they mentioned xcape which together with xmodmap looked like it could do exactly what I wanted.

So I mapped caps_lock to control_l with xmodmap, then use xcape to map control_l to escape when tapped and bingo it appears to work so far.

Cheers for the help.

---

