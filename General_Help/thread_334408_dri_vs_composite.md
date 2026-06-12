---
title: "dri vs composite"
date: 2007-01-08
forum: General Help
---

### Post by ubunus on 2007-01-08
Hello,

I've set up my ati x1600 graphic card on my workstation with the fglrx driver.
I've also installed beryl but there's a nice problem.

If I set in xorg.conf the composite flag to disabled I can run fgl_glxgears and
when I start beryl it says
``beryl: No composite extension''

If I enable the composite flag in xorg.conf both (fgl_glxgears and beryl) won't
run. Saying there's not dri modul loaded.
And it's true. In the logfile for X there's the message that composite is true
and so dri is disabled.

How to solve this?

greetings,
daniel

---

### Post by ubunus on 2007-01-08
I've posted this issue in the beryl forum.
It's more a beryl issue...

---

