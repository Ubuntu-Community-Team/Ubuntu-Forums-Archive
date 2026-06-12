---
title: "Image Magic: Convert jpg to pdf uses up entire disk"
date: 2014-09-16
forum: General Help
---

### Post by fnadde42 on 2014-09-16
I always scan papers because I like them digital and since my old scanner does not scan them directly into pdf format, I have to assemble them together with Image Magic's converter tool to merge multiple jpeg to a single pdf. It has always worked like a wonder. Until a few days ago.

My files are less that 400 MB and when I run Image Magic, it makes 42 GB of temporary files in /tmp before shutting down because of no more disk space. I have never encountered this problem before and I have scanned pages like this many times before without any problems. I don't know what's different this time so I cant figure out why it won't work.

---

### Post by mcduck on 2014-09-16
how many files there are, how large are they (in resolution, not filesize) and what command are you using to create the PDF?

Especially the DPI setting ( "*-density*") for pdf files can make a huge difference in how large the resulting file ends being (and therefore how large the temp files needed are).

Also if you are changing image sizes, or pixel density, you can often do that when opening the image rather than at the time of saving it, which of course makes things more resource friendly.

---

