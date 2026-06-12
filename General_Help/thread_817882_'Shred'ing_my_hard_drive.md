---
title: "'Shred'ing my hard drive"
date: 2008-06-04
forum: General Help
---

### Post by GammaPoint on 2008-06-04
I'm about to sell my old computer and I wanted to wipe the drive clean so that none of my private data could be retrieved by the buyer.  To do this I use the 'shred' command on my hard drive after booting up into a LiveCD. Is this correct? Is there a better way to do this?

Thanks for the help.

---

### Post by babylon2233 on 2008-06-04
Try using wipe.

Check this out

[http://wipe.sourceforge.net]("http://wipe.sourceforge.net")

---

### Post by iaculallad on 2008-06-04
Perform a low level format using the utility that your hard disk manufacturer provides.

---

### Post by Lord Xeb on 2008-06-04
You can use that software or use the following command:

```
shred -vfz -n ? (drive)
```

Were the "?" is, put the number of times you wan to shred the drive, then for were "(drive)" is, put the drive that you want to shred. Once your done, do whatever you want with it. I think that this method is more effective since you can control what is done to your drive and have immediate results.

---

### Post by Sef on 2008-06-04
There is also [Dban]("http://dban.sourceforge.net/").

---

