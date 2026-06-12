---
title: "GDK error"
date: 2005-04-04
forum: General Help
---

### Post by Gee on 2005-04-04
i'm getting these gdk errors with a couple of programs.. they were working fine a few days ago.. not really sure what to do, short of a reinstall
> ~% xmms
Gdk-ERROR **: BadMatch (invalid parameter attributes)
  serial 229 error_code 8 request_code 2 minor_code 0
~% audacity
Gdk-ERROR **: BadMatch (invalid parameter attributes)
  serial 402 error_code 8 request_code 147 minor_code 3
Gdk-ERROR **: BadMatch (invalid parameter attributes)
  serial 406 error_code 8 request_code 147 minor_code 3 

both are audio programs, but i dont know that gdk has anything to do with audio...
as far as i know these are the only ones doing it, but it seems likely that others are too

thanks in advance,
g

---

### Post by Gee on 2005-04-06
I figured out half of the problem,
the problem seems to have gone away since i turned off compositing in Xorg.

if anyone would like to explain why that was crashing my programs, I'd greatly appreciate it

thanks,
g

---

