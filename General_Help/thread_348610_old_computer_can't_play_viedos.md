---
title: "old computer can't play viedos"
date: 2007-01-29
forum: General Help
---

### Post by jdralphs on 2007-01-29
hmmm ... i'm running a laptop with i think 2-4mb of video ram, 128mb system ram, and 400mhz k6 processor with a 10gb hdd.  i'm running ubuntu edgy, with xfce, enlightenment, and gnome.

the only complaint i have is that video (dvd playback, avi, mpeg, etc...) is unplayable.  cpu usage goes to 100% and memory/swap levels stay stable.  video and sound are out of sync and then pretty much stop altogether.  any ideas?  


when i got the computer it came with a margi dvd decoder pcmcia card -- there used to be drivers available for the hardware, i contacted the author and have them now but they are for the 2.4 kernel.  if anyone wants to fix that, that would be cool too -- the tgz is here -- [http://www.tuxovision.de/margidrivers.tgz](http://www.tuxovision.de/margidrivers.tgz)

Hardware:  Margi DVD to Go pcmcia card.

i'm trying to get video to work without the hardware decoder -- i'm open to any ideas either way -- thank you!

i will repost the margi info under a different thread.

---

### Post by kairu0 on 2007-01-29
Which video sink are you using? If you are using OpenGL, try xv (or vice versa.) Also, check that DRI is running smoothly by launching glxgears.

---

