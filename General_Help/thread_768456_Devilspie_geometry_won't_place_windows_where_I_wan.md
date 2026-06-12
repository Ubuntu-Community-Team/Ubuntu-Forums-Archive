---
title: "Devilspie geometry won't place windows where I want them"
date: 2008-04-26
forum: General Help
---

### Post by IrishPidge on 2008-04-26
Hi all,

I've been trying to embed a terminal in the right-hand side of my desktop. I'm using Devilspie to set the size and location of it. Here's my .ds file:

(if

    (matches (window_name) "DesktopConsole")

    (begin

    (below)

    (undecorate)

    (skip_pager)

    (skip_tasklist)

    (wintype "utility")

(geometry "+700+50")

    (geometry "350x250")

)

) 

It won't budge from the top left hand corner, when I want it on the left! I've spent ages on this and I just don't get it. Any help would be appreciated.

---

