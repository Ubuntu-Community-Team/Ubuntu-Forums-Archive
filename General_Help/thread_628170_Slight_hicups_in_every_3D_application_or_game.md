---
title: "Slight hicups in every 3D application or game"
date: 2007-11-30
forum: General Help
---

### Post by King_Critter on 2007-11-30
So, I've got a slight problem... Every 3D game or application I run, even screen savers, hicups. By "hicup" I mean, it lags for a fraction of a second (just enough to be annoying) then goes back to full speed. It's an Nvidia Geforce 6800, and since it's rated for playing Doom 3 on "good" graphical settings, I don't see why it's lagging on a screensaver. :(

I have the latest Nvidia graphics drivers installed, and I'm running Gutsy Gibson. Please help...

---

### Post by -grubby on 2007-11-30
I don't know if this will help much, but you could type in a terminal:

```
gksudo nvidia-settings
```

and dink around in there


EDIT: wait! I think it might be an OpenGL problem

---

### Post by King_Critter on 2007-12-01
> **nathangrubb said:**
> I don't know if this will help much, but you could type in a terminal:

```
gksudo nvidia-settings
```

and dink around in there


EDIT: wait! I think it might be an OpenGL problem

Dinking around didn't help. :P 

And yeah, OpenGL was what came to my mind first, actually...

---

### Post by King_Critter on 2007-12-01
'Kay... anyone got a clue?

---

### Post by Anduu on 2007-12-01
My first guess would be something running in the background causing cpu spikes.

Try using the system monitor or top and see if there is any spikeyness going on.

---

