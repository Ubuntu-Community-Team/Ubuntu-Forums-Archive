---
title: "Flock + Pango Problem"
date: 2005-10-22
forum: General Help
---

### Post by mckirkus on 2005-10-22
I just grabbed the Flock [Developer Preview]("http://www.flock.com/developer/") and it works great until I try to use some of the new featues.  When I do it crashes and dumps the following messages:

```
Failed to load Pango module for id: 'BasicScriptEngineFc'
(flock-bin:27077): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(flock-bin:27077): Pango-CRITICAL **: _pango_engine_shape_shape: assertion `PANGO_IS_FONT (font)' failed

Pango-ERROR **: file shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
aborting...
```

The odd thing is that I have /usr/lib/pango/1.4.0/modules/pango-basic-fc.so so I'm confused about why Flock can't find it.  Any ideas?

---

