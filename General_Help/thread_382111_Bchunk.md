---
title: "Bchunk"
date: 2007-03-11
forum: General Help
---

### Post by deco57 on 2007-03-11
Well i have a .bin .cue file that i need to burn as .iso i installed bchunk and i did bchunk name.bin name.cue name
and it created a file as name.ugh
Why is it .ugh? Shouldnt it be .iso? and how can i fix this 
Thanks for your help  :)

---

### Post by xopher on 2007-03-11
If you just want to burn it, you don't need to convert it to an iso first. Any of these will burn cue/bins just fine: gnome-baker, k3b, brasero.

If you want to mount the images, you should check something called fuseiso, it mounts anything you throw at it, no problem :)

And for the original question, no idea, have you tried renaming it to .iso, just to check if it works?

---

### Post by sonicth on 2008-06-30
> **deco57 said:**
> Well i have a .bin .cue file that i need to burn as .iso i installed bchunk and i did bchunk name.bin name.cue name
and it created a file as name.ugh
Why is it .ugh? Shouldnt it be .iso? and how can i fix this 
Thanks for your help  :)

actually it's i have the same problem, it's with mode/block size i recon.

for example i have in first track: MODE1/2048, but it expects other block sizes, e.g. MODE1/2352. I am not sure but i think the extre 300bits are error correction codes, not sure if i could burn with 2048.

e.g. in the source code you have:
 if (!strcasecmp(modes, "MODE1/2352")) {
        track->bstart = 16;
        track->bsize = 2048;
        track->extension = ext_iso;


anyway you can look at the source code of the bchunk:

[http://www.filewatcher.com/p/bchunk-1.2.0-2.src.rpm.19134/bchunk-1.2.0.tar.gz.html](http://www.filewatcher.com/p/bchunk-1.2.0-2.src.rpm.19134/bchunk-1.2.0.tar.gz.html)

---

