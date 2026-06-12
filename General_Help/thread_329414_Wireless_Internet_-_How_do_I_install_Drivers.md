---
title: "Wireless Internet - How do I install Drivers"
date: 2007-01-01
forum: General Help
---

### Post by bumcheekcity on 2007-01-01
I have myself a laptop, and Ubuntu Hoary Hedgehog 5.04 or something. I've also got myself a Buffalo WLI-CB-G54A that works fine in Windows, so the card and laptop work definately. 

I've got myself some drivers from the internet, something that calls itself ndiswrapper-1.33, and it's something to do with wireless connections. I've got it, now how the hell do I install it? It's a .tar.gz file, which i understand is similar to a .zip or a .rar file, but I kind of need step-by-step instructions for it.

---

### Post by Azakus on 2007-01-01
Well, I'd first **greatly recommend** upgrading to at least version 6.06LTS "Dapper" or 6.10 "Edgy" of Ubuntu as these are much more up to date with hardware compatibility than 5.04 as you said you have. Anyway, ndiswrapper is really not a driver, it just enables drivers written for Microsoft Windows to work (somewhat decently) with Linux. That .tar.gz file is the source code, and needs to be compiled to work. However, it requires kernel development files to work, and I'm not quite sure what kernel 5.04 uses. Please paste what the ouput of this code in the terminal is:
```
uname -r
```

---

### Post by Doug11 on 2007-01-01
I followed this howto and it worked great for me. 
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

