---
title: "How much ram does Ubuntu use?"
date: 2008-05-28
forum: General Help
---

### Post by jras20 on 2008-05-28
How much Physical ram does Ubuntu use when Idle?  When I had Windows Vista on my laptop, it used between 64-70%.  I just wondered what % does Ubuntu use?  I have 1gb of ram.  Is there a program I can get to show how much is used and processor?
Thanks

---

### Post by bingoUV on 2008-05-28
This thread might help in your current and future doubts [http://ubuntuforums.org/showthread.php?t=810189&highlight=ram](http://ubuntuforums.org/showthread.php?t=810189&highlight=ram)

---

### Post by louieb on 2008-05-28
All of it. :)  you can use  **free -m **or  **top** or my favorite **htop** to find how much ram is being used for what. 
Heres a really good explanation [FAQ Linux Memory Management - Gentoo Linux Wiki]("http://gentoo-wiki.com/FAQ_Linux_Memory_Management")

---

### Post by bodhi.zazen on 2008-05-28
It depends entirely on what applications you are using.

Here is my output :

> free -m                                      05/28/08  2:15 PM
                   total       used       free     shared    buffers     cached
Mem:           502        480         21          0         77        311
-/+ buffers/cache:       **92**        409
Swap:         2180          0       2180

The -m flag == Mb.

So right now I am using 92 Mb

Those numbers do not mean much to you as you are running different applications.

Linux uses RAM very different from Windows.

    [http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)
    [http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?)

---

