---
title: "'Burn' ISO to an external Hard Drive"
date: 2007-12-29
forum: General Help
---

### Post by SuprNoodles on 2007-12-29
I'm in the process of switching to Ubuntu from Mac. One thing I'm having trouble figuring out is how to 'burn' an ISO to an external hard drive.

On OS X, I'd use Disk Utility to 'restore' an ISO to a partition somewhere on a harddrive, and 2 clicks and it was done. Though I can't seem to find a way to do the same thing on Ubuntu.

I'm not sure if there is a correct word for what I'm trying to accomplish, be it burn or restore, but I know it's not just the case of copying the files over from the ISO to the external hard drive--it involves more than that as an ISO in itself is a kind of disk partition... I think.

Any help would be much appreciated. Thanks :)

---

### Post by TidusBlade on 2007-12-29
You usually burn an ISO to a disc so Im not sure what you mean by burning it to an External HD... 
Maybe you mean extract the contents of an ISO and then move them over to another partition because that can be done easily.

---

### Post by SuprNoodles on 2007-12-29
> **TidusBlade said:**
> You usually burn an ISO to a disc so Im not sure what you mean by burning it to an External HD... 
Maybe you mean extract the contents of an ISO and then move them over to another partition because that can be done easily.

Usually you would burn to a CD, but like I say, I don't know the correct term, but basically instead of using a CD I want to achieve the same thing, but to a external hard drive instead.

The closest thing I've found is

```
dd if=/home/me/my_image.iso of=/dev/sdc1
```

Where sdc1 is my external hard drive. Is this the correct command to use?

---

### Post by TidusBlade on 2007-12-29
I never tried burning to an External HD, but if I want my content from an ISO onto another externalHD, I would just extract the ISO contents and drag it onto the destination drive, if it's an executable like a game, then I would mount it using a virtual drive.

---

