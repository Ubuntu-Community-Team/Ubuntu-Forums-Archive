---
title: "Long boot delay (A different one!!)"
date: 2007-09-29
forum: General Help
---

### Post by elmo541992 on 2007-09-29
OK, so I have 64-bit feisty, and you know the Ubuntu splash screen that comes up during boot that looks like this:
[http://news.softpedia.com/images/reviews/large/installfeistyfawn-large_003.png](http://news.softpedia.com/images/reviews/large/installfeistyfawn-large_003.png)
Well, about 4/5 of the time, it hangs at about 1-5% for around five minutes, then it boots like normal.  Its been doing this since a little after I got Ubuntu, and it's really annoying.  How can i fix this???

---

### Post by Beernut on 2007-09-29
Try viewing your logs to see what is hanging up or causing an error.  Go to "System"  > "Administration" > "System Log"

---

### Post by elmo541992 on 2007-10-04
I looked in the system log, and the delay is before it starts to log.  I actually timed it today.  The boot splash came on at 4:40, but the progress bar didn't move until 4:42.  The system log doesn't show ANY activity until 4:42.  any ideas???

---

### Post by elmo541992 on 2007-10-05
Also, the delay does happen while the splash is up, but again stays at 0%, before the system log kicks in, then it load normally.  Could something be wrong with the system log loading?

---

### Post by elmo541992 on 2007-10-07
bump

---

### Post by strabes on 2007-10-07
If you're not dual booting, when it says "loading grub" hit ESC to get into the menu. Then edit the top kernel line and remove "splash." Then boot using that line, write down the part on which it freezes, and post it back here.

---

### Post by elmo541992 on 2007-10-08
I am dual booting, but I went into recovery mode, and found where about it was freezing.  So there was a bunch of code, then I get something kind of like the following (I did it a couple of times a wrote it down, so its not super accurate

ata1.01 qc timeout ...
ata1.01 Failed to set xfermove..
ata1.01 limiting speed to udma/3:pi03...
ata failed to recover some devices retry in 5 sec...
ata1.00 ata ... resize1:(random #s)  sectors:(random #s)
ata1.00 ata ... resize1:(random #s)  sectors:(random #s)

It repeated ^that^ whole thing about 3 or 4 times.  Then, it said something like

ata disabled.

Then it boots normally.  However, whenever it does this, I just noticed, My cd-rw drive doesn't work.  I know there is nothing wrong with the drive; it works fine in windows, but only sometimes works in linux.  Is there a way I can automatically disable ata or turn on an alternative?  Also, my hard drive and cd-rw drive are on a single ide cable.  Does this help any???

---

### Post by elmo541992 on 2007-10-08
Bump.:)

---

