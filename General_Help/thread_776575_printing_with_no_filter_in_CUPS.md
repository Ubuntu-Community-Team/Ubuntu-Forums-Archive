---
title: "printing with no filter in CUPS"
date: 2008-04-30
forum: General Help
---

### Post by rajan on 2008-04-30
I'm trying to print on a konica 7145 bizhub and it's being a POS. I found the ppd file for it (Ko43245.ppd or Ko43245u.ppd in case you're wondering), but there's no filter associated with it and I apparently need a filter according to this
> 
Note that all PPD files for non-PostScript printers only work when the printers are set up with their corresponding filters and drivers.

from [http://www.linux-foundation.org/en/OpenPrinting/Database/PPDDocumentation](http://www.linux-foundation.org/en/OpenPrinting/Database/PPDDocumentation) that site. It makes me think that if I don't want to go through the hassle of finding a filter myself, i can just make a postscript and print that. that brings me to my question... how do I do that? can I use pdftops to make a postscript and then print from something like evince? will that need a filter because it's evince? i would check this, but i am home now and i'm having the problem at work. how do you (personally) print postscript docs? 

if you know anything about filters, i would also really appreciate hearing your input about how i might make my own. i'm getting the "cups-missing-filter" message and I don't know where to find a filter that will work. i'm not even sure where i can find them on my computer. i know the ppd files are in the /etc/lp/ppd folder, but i don't see any filters in there. thanks a lot,

rajan


incidentally, this is on my wife's laptop which is running 8.04, not my desktop which is the 6.06 computer that shows up on my profile.

---

### Post by Worp8d on 2008-09-23
I also am having exactly the same issue and would love to know the answer to this question.

---

