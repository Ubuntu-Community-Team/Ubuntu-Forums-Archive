---
title: "[SOLVED] Failing to make a bootable iso with mkfisofs"
date: 2008-05-09
forum: General Help
---

### Post by Ardrias on 2008-05-09
I'm having trouble making a bootable iso, and I've failed to interpret the man-pages for mkisofs. I have an ISO that I needed to edit a file in, so I extracted the ISO and edited it. 

Now I need to burn this ISO to a disc and make it bootable.

I'm doing the following: 
```

cd ~/iso
mkisofs -r -J -b isolinux/isolinux.bin -c isolinux/boot.cat -boot-load-size 4 -boot-info-table -o isodisc.iso .

```
To me this looks all fine, but it spits out an:
```
Size of boot image is 24 sectors -> mkisofs: Error - boot image './isolinux/isolinux.bin' has not an allowable size.
```

I've tried supplying -boot-load-size 24, and other various values, but it refuses to work. 

HELP!?!? :D

---

### Post by Ardrias on 2008-05-12
Bump :|

---

### Post by Ardrias on 2008-05-12
Alright, using genisoimage instead of mkisofs seems to work. Time to bandage my head after beating it against the desk...

---

