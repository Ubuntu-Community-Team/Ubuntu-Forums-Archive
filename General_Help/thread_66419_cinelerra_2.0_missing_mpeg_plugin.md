---
title: "cinelerra 2.0 missing mpeg plugin"
date: 2005-09-17
forum: General Help
---

### Post by bmgz on 2005-09-17
I have installed the new Cinelerra 2.0 and it seemed to work fine. When I wanted render an mpeg it produced an error. After tracking down the problem, it seems the /usr/lib/cinelerra/mpeg2enc.plugin is missing. Any way I can get it?

---

### Post by cgoerner on 2006-10-29
Apparently, you can copy /usr/bin/mpeg2enc to /usr/lib/cinelerra/mpeg2enc.plugin

However, after doing this, Cinelerra appears non-responsive after starting.

To work around this, I copy the file after starting Cinelerra.  I'm hoping there's a better way.

This is on Edgy Eft with Cinelerra 2.0.0-1svn20060611.1

---

