---
title: "verifying CD/DVD problem"
date: 2007-02-04
forum: General Help
---

### Post by Craftycorner on 2007-02-04
When I write, I go to verify the suckers, there's problems and the data's a mess.  

/home/craftycorner/.kde/share/apps/k3b/
++++++++++++++  from the text of lastlog.log inside

[cdrecord] Track 01:  686 of  691 MB written (fifo  98%) [buf  96%]  49.7x.
[mkisofs]  99.79% done, estimate finish Sun Feb  4 08:05:14 2007
[cdrecord] Track 01:  687 of  691 MB written (fifo 100%) [buf  96%]  51.4x.
[mkisofs]  99.94% done, estimate finish Sun Feb  4 08:05:14 2007
[mkisofs] Total translation table size: 0
[mkisofs] Total rockridge attributes bytes: 276
[mkisofs] Total directory bytes: 0
[mkisofs] Path table size(bytes): 10
[cdrecord] Track 01:  688 of  691 MB written (fifo  96%) [buf  97%]  49.8x.
[mkisofs] Max brk space used 21000
[mkisofs] 354237 extents written (691 MB)
[cdrecord] Track 01:  689 of  691 MB written (fifo 100%) [buf  96%]  51.3x.
[cdrecord] Track 01:  690 of  691 MB written (fifo 100%) [buf  97%]  49.8x.
[cdrecord] Track 01:  691 of  691 MB written (fifo 100%) [buf  96%]  51.2x.
[cdrecord] Track 01: Total bytes read/written: 725477376/725477376 (354237 
sectors).
[cdrecord] Writing  time:  157.121s
[cdrecord] Average write speed  32.4x.
[cdrecord] Min drive buffer fill was 69%
[cdrecord] Fixating...
[cdrecord] Fixating time:    2.981s
[cdrecord] BURN-Free was never needed.
[cdrecord] /usr/bin/X11/cdrecord: fifo had 11427 puts and 11427 gets.
[cdrecord] /usr/bin/X11/cdrecord: fifo was 0 times empty and 4976 times full, 
min fill was 28%.

How do I clean this mess? :(

---

### Post by MoLE on 2007-02-11
Can't see any errors reported there - seems like a successful write.

A couple of things you can try:
- use k3b to create your CD, but burn the CD to an ISO file
- burn the ISO using nautilus cd-writer (just right-click and select write to CD)

Limit your burn speed (drop it down to 16x or around there)

---

