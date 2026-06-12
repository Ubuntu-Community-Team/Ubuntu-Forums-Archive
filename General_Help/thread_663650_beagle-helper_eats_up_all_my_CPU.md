---
title: "beagle-helper eats up all my CPU"
date: 2008-01-10
forum: General Help
---

### Post by willix on 2008-01-10
Hy
I wondered if anyone has the same kind of problem and how I might try and solve it.

Each time I log on to my Ubunto Edgy, after a while, the beagle-helper process eats up all my CPU and never releases it.
I figure the process was indexing my system or something but even after leaving it running for a whole night, it was still cosuming over 80% of the CPU (the rest being shared by other deamons).

Any idea, comments, suggestion as to the cause and to how to avoid this? 

tx
w.

---

### Post by sancho panza on 2008-01-10
I think this is a known issue with beagle. Thats one of the reasons why gutsy uses Tracker. I dont know how to fix it, other than getting rid of it, and installing tracker, maybe. Or install gutsy if u can...Anybody else?

---

### Post by dbera on 2008-01-10
> **willix said:**
> Hy
I wondered if anyone has the same kind of problem and how I might try and solve it.

Each time I log on to my Ubunto Edgy, after a while, the beagle-helper process eats up all my CPU and never releases it.
I figure the process was indexing my system or something but even after leaving it running for a whole night, it was still cosuming over 80% of the CPU (the rest being shared by other deamons).

Any idea, comments, suggestion as to the cause and to how to avoid this? 

tx
w.

Beagle in edgy has several known problems that can cause this behaviour with certain files. There are updated packages for edgy, you can try them:
[http://beagle-project.org/Ubuntu_Installation](http://beagle-project.org/Ubuntu_Installation)

---

### Post by willix on 2008-01-11
Thanks dbera

I found an edgy repository from the beagle project web site and was able to smoothly ugrade to a new version (which is not in the official ubuntu edgy repositories) and that has done the trick; well it looks like it anyway: I left wy laptop on for part of the night and the CPU was normal when I went back to it (no hungry beagle-helper process running :)

---

