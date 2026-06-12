---
title: "Celestia is very hungry! (hogging the CPU)"
date: 2006-12-17
forum: General Help
---

### Post by hotani on 2006-12-17
When I start up Celestia, it starts pulling about 60% of my CPU - and that is on a dual core system, which means one core is pegged at 100% while the other is around 25% or so.

Why is it doing this? It is also very sluggish and it was not like that before. I tried reinstalling which seemed to fix the sluggishness but I would still see the CPU usage. Now after running the recent Edgy updates it is sluggish again. 

Fixes?

---

### Post by hikaricore on 2006-12-17
Are your video drivers setup properly?

```
glxinfo | grep rendering
```

Should output something like this:

> direct rendering: Yes

---

### Post by hotani on 2006-12-17
Yep. Video drivers are working great - Quake 4, Beryl - all fine.

My (louder than a tornado outside) GPU fan spins up when Celestia starts but it is still munching up the CPU.

---

### Post by Ramses de Norre on 2006-12-17
The same thing here, it keeps my cpu on 99-100% while running.
I've got an amd64 3700+ and ati x600 graphics with fglrx..

---

### Post by hotani on 2006-12-17
Here's what I'm running: 3800+ AMD, GeForce 7600 GT

I've been just opening Celestia when I need it (yes, I need it!), then closing it after I find what I'm looking for. It would be nice to be able to keep it open while I'm working. At least it runs!

---

