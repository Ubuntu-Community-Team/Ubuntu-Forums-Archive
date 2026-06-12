---
title: "ubuntu dead ????"
date: 2007-01-04
forum: General Help
---

### Post by mistypotato on 2007-01-04
Well,

Today I had my first application crash.

Everything was fine and then I attempted to open a media player (RhythmBox Music Player).

The system stopped responding and never recovered so eventually I had no choice but to shut down and re-start.

Problem is...it won't restart :mad: 

During Boot up it stops on "Starting Enterprise Volume Management System".

Please don't tell me I have to re-install everything just because one lousy application caused a problem??????

Help!??

---

### Post by shakin on 2007-01-04
When you shut down were you able to shut down properly, or did you have to use the power button on your computer?

It's possible, though unlikely, that using the power button can cause corruption on the hard drive. I've never actually had that happen to me and I've done hundreds of power-offs in my life.

1. On the Grub screen do you have another kernel choice? You can try selecting a different kernel and seeing if that works.

2. Does booting into recovery mode work?

3. Try booting with a live cd, mounting your / partition and running fsck on it.

---

### Post by mistypotato on 2007-01-04
Thanks!

I'll try these things

---

