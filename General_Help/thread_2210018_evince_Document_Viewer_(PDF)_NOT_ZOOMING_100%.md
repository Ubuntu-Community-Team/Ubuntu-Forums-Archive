---
title: "evince Document Viewer (PDF) NOT ZOOMING 100%"
date: 2014-03-08
forum: General Help
---

### Post by jp734 on 2014-03-08
Everytime I use evince PDF viewer and try to zoom at 100% or larger, it only goes uo 90%. I use it to QC a large drawing, about 3' by 4', and I can't see the text clearly. It is too smal to read.

Any clues? I am using Lubuntu 13.10 and the system spec is Core2Quad 2.83 GHz with 4GB or ram and SWAP size is 3.9 GB.

Thanks in advance.

---

### Post by sudodus on 2014-03-08
I think Okular is more powerful, but it will bring a lot of KDE libraries, which is OK if you have disk space. install it via the repos

```
sudo apt-get install okular
```

Read about it here [http://http://okular.kde.org/](http://http://okular.kde.org/)

---

### Post by jp734 on 2014-03-17
- Downloaded Adobe Reader 9 from adobe's website (filename.bin)
- chmod +x filename.bin
- sudo ./filename.bin and follow directions

Works perfectly. Zoom up to 6000% and fast. I was beginning to worry about my quad core system with 4GB of ram. I thought I would need to upgrade again. Thank goodness I was wrong. :D

---

