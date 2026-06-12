---
title: "How to use BadRam?"
date: 2008-02-21
forum: General Help
---

### Post by Eestlane on 2008-02-21
Hi,
Firstly, I need to ask if Ubuntu 7.10 already include BadRam? If so, then...
I know that to ignore the bad ram I need to edit the menu.lst file of grub, i.e adding to the end of the kernel line:
```
badram=0x3a00b918,0x3a00b918
```
Or well, that's what I found after Googleing.

However, I had MemTest86 in the time I had no Linux in it, and only have an image of the results, it includes not badram= specific values, so could anyone tell me what do I have to write after badram=

I attach the image.


I am very grateful whoever answers my questions, thanks in advance!

---

### Post by seventhc on 2008-02-21
I thought you had to replace ram that has gone bad.
No???
Even if you can ignore it, it is only a temporary fix.
If your ram is bad, I suggest just replacing it now.

---

### Post by Eestlane on 2008-02-21
Sorry, man, no money. I would actually like to see how well BadRam works.
If no-one can convert this memtest result to something acceptable for badram=..., then I probably have to run it again and to see the badram=... line press C?

EDIT: So, I ran memtest again, and it luckily took below 30 mins for one time through all the tests to run and I got the hole from quite beginning. And chose to parse the badram aswell, so it was:
```
badram=0x1c749ffc,0xfffffffc
```

---

