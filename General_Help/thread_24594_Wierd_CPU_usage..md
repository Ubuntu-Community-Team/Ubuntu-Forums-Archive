---
title: "Wierd CPU usage."
date: 2005-04-07
forum: General Help
---

### Post by spacemonkey on 2005-04-07
I put this in the apps section because I figure it's got something to do with apps.  I recently upgraded from Warty to Hoary and I'm getting some strange spikes in CPU usage, and its running hotter than normal.  In warty it idled really low, 0 to 10%, and spikes when opening windows were not very big, but in Hoary, it idles 15-25, and spikes sometimes to 95% when I open stuff.  I've got the exact same stuff running as I did in Warty, which include firefox, one terminal, gaim, amarok, and gkrellm all open at the same time.  My CPU is a P4 2.8 ghz with hyperthreading.  I don't really understand why Hoary would take up so much more system resources.  It's not really a problem yet....I'm more curious than worried.  Any suggestions?

---

### Post by Klin'Targ on 2005-04-08
Check to make sure something didn't screw up DMA. If DMA is off, it could explain large CPU spikes when opening new windows.

```
sudo hdparm /dev/<hard disk partition>
```

---

