---
title: "Batch converting images to bitmap mode with 50% threshold filter"
date: 2013-10-30
forum: General Help
---

### Post by vap1485 on 2013-10-30
Greeting all. I'm working on reprinting and publish an old book thats out of print, and I need to clear up some of the pages that I scanned.

My printer tells me that I need to convert the images to bitmap mode with 50% threshold filter. They say I have to use photoshop or indesign, but I don't believe them. I'm pretty sure imagemagic or even "convert" command can batch convert all 100 or so pages with relative ease. 

[SIZE=7][[IMG]https://en.bitcoin.it/w/images/en/c/c0/F33980a445.png[/IMG]]("https://en.bitcoin.it/wiki/File:F33980a445.png")1,000,000 [/SIZE][SIZE=7] question:[/SIZE]

**what's the command?**

---

### Post by Vaphell on 2013-10-30
convert inputfile -threshold 50% outputfile

more ways to skin the cat
[http://www.imagemagick.org/Usage/quantize/#two_color](http://www.imagemagick.org/Usage/quantize/#two_color)

---

### Post by vap1485 on 2013-10-30
thanks. worked like a charm

---

