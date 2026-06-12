---
title: "Evince not printing some PDF files"
date: 2008-05-06
forum: General Help
---

### Post by nelfer on 2008-05-06
Hi,

I'm using Ubuntu 7.10.

For some reason Evince doesn't want to print some PDF files. When I send them to the printer nothing happens. Then i tried sending it to the Cups PDF printer and I saw why: Empty pages were sent.

This seems to happen with PDF files with graphics in color. I don't recall any "text only" or "black and white" PDF that didn't print. I only recall color PDFs not printing. However, if I use pdf2ps and then try to print the resulting PS file, it prints fine.

The interesting thing is that I can see the PDF perfectly on the screen, but when sending to the printer, only empty pages come up.

---

### Post by cmnorton on 2008-05-06
It's a bug. that is supposedly fixed in Hardy. 
[https://bugs.launchpad.net/bugs/212017](https://bugs.launchpad.net/bugs/212017)

---

