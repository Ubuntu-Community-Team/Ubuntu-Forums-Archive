---
title: "eterm fonts size n color"
date: 2005-04-07
forum: General Help
---

### Post by lizardking on 2005-04-07
I tried **Eterm** and it is rocks (I set it with traspatencies and without borders) nut i cannot read well the very small fonts?

How can I change the size and also the colo???

some help? :-?

---

### Post by brox on 2005-04-08
This is what I use:

-------------------------------------------------------------------------------------------------------------------------
--trans -x --geometry 75x25+0-300 -s --scrollbar 0 --buttonbar off -c cyan -f cyan --font-fx none
--------------------------------------------------------------------------------------------------------------------------

So, -c color will change cursor color and -f color for font color. --font-fx none will get rid of the fuzzy fonts if you are using transparent Eterm with a light background.

Hope this helps...

---

