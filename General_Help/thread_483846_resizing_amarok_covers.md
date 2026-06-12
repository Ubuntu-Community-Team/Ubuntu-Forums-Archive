---
title: "resizing amarok covers"
date: 2007-06-25
forum: General Help
---

### Post by pickarooney on 2007-06-25
I'm getting lag messages from replaygain, advising me to reduce/remove the large album cover images. 
Is it OK to just go into the **~/.kde/share/apps/amarok/albumcovers/large** directory and run
```

mogrify -geometry 100x100 *

```
?

The files in there have no extensions but **file** tells me they're PNGs.

Unless there's a more 'orthodox' way of doing this?

---

