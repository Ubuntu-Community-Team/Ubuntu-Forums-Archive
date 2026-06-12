---
title: "Evince memory problems when zooming..."
date: 2007-10-29
forum: General Help
---

### Post by GrouchoMarx on 2007-10-29
There are a few posts already about evince and it's memory management issues. However  this specifically relates to memory issues when zooming. For instance, a 300 page text-only document more than doubles memory usage with each zoom: 29MB @ 100%, 96MB @ 200%, and 185MB (!!!) @ 300%. A ONE page text document goes from 11MB to 44MB to 82MB (!!!) at those same zoom levels. I was trying to open a public transit route map (a pretty detailed pdf), and by zooming once it basically used up all the system memory and the swap space, which is unbelievable. I would just chalk it off to a memory leak, except for the previously described behavior with smaller files.

So, is this an evince thing, or a pdf thing? If it's an evince thing, can anyone suggest a better reader under Linux?

---

