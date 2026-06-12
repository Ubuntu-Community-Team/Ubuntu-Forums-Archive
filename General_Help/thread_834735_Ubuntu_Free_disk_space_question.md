---
title: "Ubuntu Free disk space question"
date: 2008-06-19
forum: General Help
---

### Post by jras20 on 2008-06-19
On this screenshot, does this mean I have 27.0gb free?  
Thanks

---

### Post by NilsE on 2008-06-19
That is what it looks like. Do you have reason to suspect otherwise?

---

### Post by iaculallad on 2008-06-19
If you're still in doubt :) about your drive space statistic, try running **df -h** in your terminal or you can use the **discus** utility available in the repo. Compare the results with your Disk Usage Analyzer result.

```
df -h
```

For discus:

```
sudo apt-get install discus
```

To execute:

> discus

---

### Post by jras20 on 2008-06-19
> **NilsE said:**
> That is what it looks like. Do you have reason to suspect otherwise?

Thanks...
Thats what I thought also, when I tried to copy a dvd it told me that the disk was full.  I don't know if it just loaded wrong or what.  I use Brasero disk burning to copy/write/back up my stuff.   I may have a setting wrong or something?  It may of tried to start writing on the DVD that already had data on it?

---

### Post by init1 on 2008-06-19
> **jras20 said:**
> Thanks...
Thats what I thought also, when I tried to copy a dvd it told me that the disk was full.  I don't know if it just loaded wrong or what.  I use Brasero disk burning to copy/write/back up my stuff.   I may have a setting wrong or something?  It may of tried to start writing on the DVD that already had data on it?
Where you trying to copy something to a DVD, or trying to copy a DVD to your hard drive?

---

### Post by avtolle on 2008-06-19
Was there something on the DVD? Brasero reports a full disk if the medium to which writing is to be had is full (or not full, but not left open, etc.), and if rewritable, offers to blank it and proceed.

---

### Post by jras20 on 2008-06-19
Yeah it was a movie I made from a VHS from my DVD recorder.  The strange thing was yesterday it copied another dvd fine.

---

### Post by jras20 on 2008-06-20
Does K3b The cd dvd kreator come with Ubuntu installing?  I can't remember I like that program.

---

### Post by avtolle on 2008-06-20
You can add it from the repositories using either Synaptic or Add/Remove programs. Installing it will also install a bunch of KDE libs, but only enough to make K3b usable in the Gnome environment.

---

### Post by 7raTEYdCql on 2008-06-20
When you open Nautilus in your home directory then what is written at the bottom will be the amount of disk space available to you.

I think the rest is what is used by root and eventhough it is free isnt accessible to you.

---

