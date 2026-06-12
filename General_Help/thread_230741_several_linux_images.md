---
title: "several linux images"
date: 2006-08-06
forum: General Help
---

### Post by kno712 on 2006-08-06
Hello!

when I do 

[FONT="System"] dpkg -l | grep linux-image[/FONT]

I get the following:

[FONT="System"]ii  linux-image-2.6.15-23-386              2.6.15-23.39                            Linux kernel image for version 2.6.15 on 386
ii  linux-image-2.6.15-26-386              2.6.15-26.46                            Linux kernel image for version 2.6.15 on 386
ii  linux-image-386                        2.6.15.24                               Linux kernel image on 386.[/FONT]

is everything Ok? Should I search and delete some of them and keep the last one?

Thanks a lot.

---

### Post by 23meg on 2006-08-06
The last one is a metapackage. You can just keep the most recent one and safely delete the rest if it's working.

---

### Post by Ramses de Norre on 2006-08-06
I'd keep more than one kernel, in case the latest starts acting strange after an upgrade (has happened to me allready and I was glad I had an older one still installed;))

---

### Post by 23meg on 2006-08-06
You can always boot in recovery mode and install another kernel, or use the live CD to do so.

---

### Post by kno712 on 2006-08-06
Ok, thanks for your help. 

So let's say that the last acts strange (this is linux-image-2.6.15-26-386 2.6.15-26.46). How can I install the previous one? Everything is working correctly (cross my fingers!) I just want to know more.

Thanks in advance.

---

