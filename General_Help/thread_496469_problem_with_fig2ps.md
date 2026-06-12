---
title: "problem with fig2ps"
date: 2007-07-09
forum: General Help
---

### Post by somitras on 2007-07-09
:(I have installed TexLive and fig2ps on my system. (By default I had tetex which I changed to TexLive). Now when I try to convert a .fig file containing some special latex symbols into ps using gif2ps, I get "latex error" and the figure doesn't get converted into ps. The special text symbol that i am using is very simple, just $a_b$ and I expect to see a subscript b in the ps file.

Interestingly, another computer having same Ubuntu config but with Tetex instead of TexLive converts the fig file to ps properly.

Could someone please help solve this problem.

Commands that I used and their output :

$ xfig -specialtext temp.fig 
$ fig2ps temp.fig

This is fig2ps version 1.3.6, Copyright (C) 2004-2006 Vincent Fourmond
fig2ps comes with ABSOLUTELY NO WARRANTY. This is free software, and you are welcome to redistribute it under the conditions stated in the GPL.txt file in the source archive.
Processing file temp.fig
This is pdfeTeX, Version 3.141592-1.30.5-2.2 (Web2C 7.5.5)
entering extended mode
Conversion failed for file temp.fig:
        Problems with latex: command returned 256

---

