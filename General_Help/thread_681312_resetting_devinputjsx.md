---
title: "resetting /dev/input/jsx"
date: 2008-01-28
forum: General Help
---

### Post by rm-rf on 2008-01-28
I'm using Logitech Joysticks which are working fine but for this problem. 

First one connected gets assigned to /dev/input/js0, second one to /dev/input/js1, so on so forth.

I use qjoypad custom map the keys to keyboard inputs. input from /dev/input/js0 has one map, /dev/input/js1 another.

Say  I disconnect the one on /dev/input/js0. js0 disappears and there is only js1.

Say I connect the joystick back. Now I have /dev/input/js1 and /dev/input/js2. If I keep disconnecting and connecting it back, it just assigns a new number instead of reusing the lowest one not being used.

This messes up the key mapping software, as it is still mapping just for /dev/input/js0 and js1, which makes the whole plug-n-play rather moot. 

Is there a way to force it to use /dev/input/js0 and /dev/input/js1 regardless of whether the joystick gets disconnectedr?

---

### Post by rm-rf on 2008-01-30
bump

---

### Post by rm-rf on 2008-02-12
bump

---

### Post by rm-rf on 2008-02-15
bump

---

