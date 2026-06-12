---
title: "CD Ripping"
date: 2004-11-05
forum: General Help
---

### Post by paul.hendrick on 2004-11-05
i've been wondering why cd ripping is so much slower on linux, than is it on Mac OSX? it seems to be at least 5 times slower to rip a cd to mp3, and even worse for ogg.
i'm using cdparanoia and lame, and i've tried cdda2wav also(with very small speed increase). this is even with nice set to -20

is it just that the free encoders are slower than proprietary ones, or are there any tricks to it?

thanks,
paul.

---

### Post by diebels on 2004-11-05
Is dma enabled for the cd-rom?

---

### Post by paul.hendrick on 2004-11-05
even after enabling dma on the drive, it's painfully slow. 4 - 5 minutes to rip a 4 minute track.

---

### Post by paul.hendrick on 2004-11-05
actually, i am noticing a speed boost now. it's taking around 1 minute to rip a 4 minute track with cdparanoia. is that a decent time?
grip shows the speed of the rip going between 4.0 and 5.0 on a drive that i think is a 48 speed cdr/dvd.
do those speeds seem correct?

[QUOTE=paul.hendrick]even after enabling dma on the drive, it's painfully slow. 4 - 5 minutes to rip a 4 minute track.[/QUOTE]

---

### Post by diebels on 2004-11-05
Even when you use "lame --preset fast standard", and cdparanoia -Z? Maybe you need -S option to cdparanoia if it's not detecting speed properly.

Don't know what codecs you use in OSX, could very well be that they are made for speed, or maybe they're better at using powerpc prosessor instructions?

Speed ratings for drives is max, not constant. And the rating is for data tracks. Most are much slower at audio tracks. Plextor drives are known for very high audio reading speed, while cheaper drives are normally very slow at audio.

---

