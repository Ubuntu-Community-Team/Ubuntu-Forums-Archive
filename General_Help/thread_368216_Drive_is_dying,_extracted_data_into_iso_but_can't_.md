---
title: "Drive is dying, extracted data into iso but can't access it"
date: 2007-02-23
forum: General Help
---

### Post by herzzreh on 2007-02-23
Hi,

I started getting bunch of buffer i/o errors... I copied the data using dd onto a different partition into an iso file but I can't mount it.

When I do mount -o loop /iso/file /mount/point it says something along the lines of wrong filesystem, wrong something, bad superblock or something like that..

Any solutions?

---

### Post by Muzik83 on 2007-02-23
Perhaps someone else can comment on this solution _before_ you try it

dd does not create an ISO of the filesystem, but rather a raw image of it (slight difference).

You can try a 
mkisofs -o my_iso.iso /path/to/your/dd.image

to make an iso of your image.  This may not work, as it's just a stab in the dark at a solution.  

Anyone else care to comment on this idea?

-sean

---

### Post by Muzik83 on 2007-02-23
Sorry, bad idea.  Lastnight I un-tarred my backup and when I tried that thismorning it didnt work.

What type of filesystem was inside it, was it Linux & EXT3?

---

### Post by herzzreh on 2007-02-25
Hi!

It was Linux and reiser. Drive itself is, well, half fine - it sucks that the partition holding /home crapped out.

---

