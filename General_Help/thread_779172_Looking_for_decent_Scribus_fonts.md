---
title: "Looking for decent Scribus fonts"
date: 2008-05-02
forum: General Help
---

### Post by arnicainthemembrane on 2008-05-02
I have been having a hard time using Scribus with Ubuntu 'cause the program doesn't seem to like exporting documents to PDF with the fonts that came with Ubuntu and the various packaged programs (Gimp, OpenOffice, etc.) I'm wondering how I can find fonts in the repositories which might work well with Scribus, if anyone has had this issue, and if there are any suggestions. Thanks.

---

### Post by p_quarles on 2008-05-02
Generally speaking, graphics and print work gets easier with the MS truetype fonts installed:
```
sudo apt-get install msttcorefonts
```

You may also like Red Hat's Liberation truetype fonts (available in the Ubuntu multiverse repository).

---

### Post by arnicainthemembrane on 2008-05-26
So i did download the suggested fonts, but then I tried scribus and as usual it wouldn't export to pdf. The people I consulted about the problem found that it could be solved by having the right fonts, they were able to take documents I had made, change around the fonts then send them back to me in pdf format no problem.

how can I know that the fonts i just downloaded are being used by Scribus? Is it automatic? How in scribus can I ascertain whether or not I'm using fonts which will work? Is it all trial by error?

---

