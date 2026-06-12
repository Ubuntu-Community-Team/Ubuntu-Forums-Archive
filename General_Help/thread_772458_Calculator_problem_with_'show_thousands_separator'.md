---
title: "Calculator problem with 'show thousands separator'"
date: 2008-04-28
forum: General Help
---

### Post by pholden on 2008-04-28
When turning on *Show Thousands Separator* in the Calculator (gcalctool) the output is going a little crazy 8-[

See attached screenshots - typing a simple calculation such as 600*200 produces the following display.

6,00*,200
= 1,20,,000

Is there a way to fix this?

---

### Post by Koroviev on 2008-04-28
Looks a bit like bug #208260. If you feel like compiling from source you can try the patch in launchpad. If not, probably there will be an update in the near (or not so near) future.

---

