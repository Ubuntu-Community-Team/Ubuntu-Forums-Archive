---
title: "Speeding up gutsy?"
date: 2007-11-23
forum: General Help
---

### Post by TechMansoor on 2007-11-23
What would you guys suggest? I'm running a 3.0p4 hyper threaded with a gig of memory. I dont think its being utilized properly. What would you guys suggest? I'm also running kde which I think is a little slower than gnome? How can I speed up my kde basically?

---

### Post by knutschr on 2007-11-23
I have a 3.2 GHz dual CPU with 2 GB RAM.
I followed this guide:
[http://ubuntuforums.org/showthread.php?t=107856&highlight=boost+system](http://ubuntuforums.org/showthread.php?t=107856&highlight=boost+system)

The result was incredible! (Allthough my Kubuntu was fast enough beforehand).

Be sure to change the drive properly in the commands.
If you get any errors, do the command again with your changes.

(Probably your drive, hda instead of sda may be)

---

### Post by TechMansoor on 2007-11-23
> **knutschr said:**
> I have a 3.2 GHz dual CPU with 2 GB RAM.
I followed this guide:
[http://ubuntuforums.org/showthread.php?t=107856&highlight=boost+system](http://ubuntuforums.org/showthread.php?t=107856&highlight=boost+system)

The result was incredible! (Allthough my Kubuntu was fast enough beforehand).

Be sure to change the drive properly in the commands.
If you get any errors, do the command again with your changes.

(Probably your drive, hda instead of sda may be)

Before I do this, were there any errors(fatal) you encountered that needed correcting before everything was finalized?

---

### Post by knutschr on 2007-11-23
Yes. In the 2 commands witth tune2fs.., I just copied hda1 as my drive instead of correcting it to sda1
I then got error messages, which I ignored.
That gave the result X would not start.
I then started Security mode, red the post by connecting to Internet with my mobile, entered the correct codes on the PC, restarted, and what a surprise :)

---

