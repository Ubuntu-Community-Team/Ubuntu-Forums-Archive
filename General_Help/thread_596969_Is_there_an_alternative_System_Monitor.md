---
title: "Is there an alternative System Monitor"
date: 2007-10-30
forum: General Help
---

### Post by amorangi on 2007-10-30
I have a quad-core/2GB RAM, but every now and then my system runs very slowly. But when I look at the system Monitor it shows all cores at 10% or less, 300GB or so RAM used, and a similar amount of swap. There is nothing to indicate what could be killing the system, though I suspect IRQs/disk thrashing. Is there anything that will display more info about the system so I can find what is giving me grief?

---

### Post by forestpixie on 2007-10-30
you could try top in a terminal

---

### Post by amorangi on 2007-10-30
Thanks, %hi in top is probably what I was after

---

### Post by Gen2ly on 2007-10-30
SystemMonitor will show you the nice process (the I/O of the disk)  at times slocate and possibly some other programs work in the background.  By default, the nicecolor is similar to the blue default.  If you want to do more advanced look into conky or gkreallm.

---

### Post by amorangi on 2007-10-31
Conky is the best so far. Strangely it's only reporting 1.3MB/s I/O though when the hard drive is being thrashed and I'm on go slow. It's also swapping out to swap when it shouldn't be - it's reporting 300MB RAM in use, 300MB or so swap. It shouldn't be doing this when theres 1.7GB available!

---

### Post by kah00na on 2007-10-31
Have you looked into hdparam?  It allows you to change some parameters on your harddrive to help speed it up.

---

### Post by kah00na on 2007-10-31
Here's a website that explains more.  I used this on my myth box and it really sped up my disk reads and writes.

[http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html]("http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html")

---

### Post by notatoad on 2007-10-31
> **amorangi said:**
> is there an alternative system monitor

come on.  in linux there is an alternative EVERYTHING :)

---

### Post by newlinux on 2007-10-31
I like htop, especially since it runs from terminal...

---

