---
title: "Can not burn data DVDs (and maybe other things as well) with k3b"
date: 2007-07-17
forum: General Help
---

### Post by McSnuffy on 2007-07-17
I'm on a pretty fresh install of Fiesty (Ubuntu server edition with kde-core) right now and pretty much everything works (having truecrypt troubles that I never had with 6.06, but that's a different story). Anyway, I am trying to burn a simple data DVD in k3b, but I get an error even before the writing starts. My burner and the disc inside of it seem to be recognized just fine, I add the files without a problem, and then I click "burn" which produces an error that says "could not determine the next writable address" almost instantly. I've attached the debug message as well:

```
System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-15-server
Devices
-----------------------
TSSTcorp DVD+-RW TS-L632H D200 (/dev/hda, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]


```

Anybody here know what the problem could be? I feel that I am making a very simple mistake, but I don't really know, as I have never burnt anything using k3b before. If you need more info from me, please ask. I'd like to figure this one out. Thanks for reading.

---

### Post by McSnuffy on 2007-07-17
For the record, I have tried this with my laptop's DVD burner and my old external USB DVD burner, and they both produce the same error, leading me to believe that this isn't hardware-related.

---

