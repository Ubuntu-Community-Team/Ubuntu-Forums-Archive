---
title: "x2go disable pulseaudio"
date: 2017-08-10
forum: General Help
---

### Post by Jason_Hunter on 2017-08-10
I'm connecting to an ubuntu-16.04 with x2go from a windows system and no matter what I try, I always get audio on the windows machine. I want audio to exit on the local ubuntu computer, not the windows computer. 

I've tried everyting, but I always hear audio on the windows system. 

Is there no setting to disable this?

Can I disable something on the ubuntu system to make it play locally?

---

### Post by Jason_Hunter on 2017-08-10
ok, the whole problem is that x2go sets a variable that fscks up pulseaudio, so do this: 

unset [FONT=gotham]PULSE_CLIENTCONFIG && pulseaudio[/FONT]

---

