---
title: "How to find gaps in a sequence of files ?"
date: 2012-10-23
forum: General Help
---

### Post by jfl on 2012-10-23
I don't really know how to say it, so I'll give an example.

I have a list of files in a directory that are named "PICT100xxxx.jpg", starting at "PICT1000100.jpg", and ending at "PICT1002661.jpg". There should be around 2562 files.   There are about 150 missing. Is there a way to find the breaks in the sequence ?
I was thinking to put the file list in a .txt file and then to parse it, with a perl routine, comparing each with previous.  I have not written a line of code for the last 5 years ...  Must be an easier way.

Thanks

---

### Post by steeldriver on 2012-10-23
I think you could do something like

```
for file in PICT{1000100..1002661}.jpg; do [ -f "$file" ] || echo "$file" not found; done
```

---

