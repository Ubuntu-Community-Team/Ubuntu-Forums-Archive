---
title: "Lives Video Editor Hangs on startup"
date: 2006-08-21
forum: General Help
---

### Post by mister_p_1998 on 2006-08-21
Trying to install this app, but it hangs on startup.
The website to do the following if it happens:

edit ~/.lives, and change:

<jack_opts>
0
</jack_opts>

to:

<jack_opts>
16
</jack_opts>


Then restart LiVES as normal.


Where is ~/.lives?
cant find it anywhere?

---

