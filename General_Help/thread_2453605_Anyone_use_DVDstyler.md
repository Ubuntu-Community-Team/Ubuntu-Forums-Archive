---
title: "Anyone use DVDstyler?"
date: 2020-11-13
forum: General Help
---

### Post by newb85 on 2020-11-13
So I've been using DVDStyler for years to put our family videos onto an annual DVDs.  I wouldn't say it was a slick experience in the past, but this year, I'm finding myself beating my head against the desk trying to get it to work.  Specifically, whenever the finished DVD reaches the end of titleset 1, it jumps back to the root menu.This is with version 3.1 from panda jim's ppa.  I'm on (a version of) 20.04.

---

### Post by newb85 on 2020-11-13
I think I found the main problem.  In the propertis of the "Play All" button on the main menu, "Single Titleset" was selected, instead of "All Titlesets". now, when generating the .iso, I get a parse error that says title 104 is out of range.  Thing is, I don't have more than 99 titles in any of my titlesets.  (The software wouldn't let me import that many.)

---

### Post by HermanAB on 2020-11-13
Sounds like the author never thought anyone would make that many DVDs and there is an overflow condition somewhere.  You need to install the source code and debug it!

---

### Post by ActionParsnip on 2020-11-14
Have you tried devede? May work for. Just a suggestion

---

### Post by vmpx on 2020-11-15
Try QDVDAuthor.

---

### Post by newb85 on 2020-11-27
> **HermanAB said:**
> Sounds like the author never thought anyone would make that many DVDs and there is an overflow condition somewhere.  You need to install the source code and debug it!
Actually, I believe it's an overflow condition on the number of titles (clips) in a titleset.  In this case, I've been very careful in the project at hand not to exceed 99 per titleset.

---

### Post by vmpx on 2020-12-18
You can also try bombono-dvd (software.opensuse.org)

---

### Post by csae2608 on 2020-12-23
i used it , it functions, but had various attemps to be made, with different results under macos, windows or linux.
cannot say it is a perfect solution, but for a free software it is good. it seems buggy sometime, but i was able to make one DVD with ttitles that would pack exactly one 1 DVD as desired.

---

### Post by grxgghxrpxr on 2020-12-23
I can't even install it...

---

