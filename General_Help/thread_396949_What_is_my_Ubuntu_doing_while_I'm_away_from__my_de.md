---
title: "What is my Ubuntu doing while I'm away from  my deak?"
date: 2007-03-30
forum: General Help
---

### Post by diablo75 on 2007-03-30
I added a system monitor to the system bar at the top of the screen, and noticed that while I was away, the CPU was in heavy use.  I didn't leave the computer doing anything processor intensive.  What kind of background services might Ubuntu be running?

Just curious.  Thanks.

---

### Post by Titus A Duxass on 2007-03-30
Enter "top" in a terminal to see what's being run, probably the updater.

---

### Post by Fungyo on 2007-03-30
Could it be file indexing? Something like Beagle would index your files when your pc is idle.

---

### Post by Abandon on 2007-03-30
> **diablo75 said:**
> I added a system monitor to the system bar at the top of the screen, and noticed that while I was away, the CPU was in heavy use.  I didn't leave the computer doing anything processor intensive.  What kind of background services might Ubuntu be running?

Just hit that systemmonitor with you're mouse. Than tap the 2nd tab, click on the 
%cpu and see for you're self. Or (better) use the top command in a terminal.

Cheerio

---

### Post by diablo75 on 2007-03-31
Turns out it's Beagle running in the background, probably doing indexing.  But you know, I don't think I've ever used Beagle.  How do I access it?

---

### Post by Djembe on 2007-04-02
it's the search utility

---

