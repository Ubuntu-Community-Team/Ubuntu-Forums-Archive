---
title: "Evince-thumbnailer ignoring size parameter?"
date: 2006-09-18
forum: General Help
---

### Post by ifokkema on 2006-09-18
Hi,

I'm trying to have evince-thumbnailer generate bigger thumbnails. The problem is the thumbnails it does create look bad (no anti-aliasing) so I want to create a bigger thumbnail, that I could resize by using ImageMagick (the idea is to script the whole thing eventually).

Either way, it generates thumbnails of around 74x99 pixels (seems to differ a little among PDF files). But it's supposed to accept a size:

```
  14:00:43 ifokkema@5-HKG-02-0098:~$ evince-thumbnailer -h
Usage: evince-thumbnailer [-s <size>] <input> <output>
```
However:
```
  13:57:37 ifokkema@5-HKG-02-0098:~$ evince-thumbnailer -s 200 /path/to/input.pdf ./test.png
```
Generates small, unreadable thumbnails. I've tried different numbers, and all I learnt was that values below 40 are not accepted...

Any ideas on how to fix this?

Thanks in advance!

---

