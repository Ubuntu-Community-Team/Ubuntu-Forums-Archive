---
title: "Missing &quot;/usr/include/X11/keysym.h&quot; from XBindKeys"
date: 2014-09-19
forum: General Help
---

### Post by Tinker Tantrum on 2014-09-19
I am missing the "/usr/include/X11/keysym.h" and "/usr/include/X11/keysymdef.h" files from XBindKeys. Is there an alternative way to install them?

---

### Post by steeldriver on 2014-09-20
I'm not sure what you mean by "alternative way" - have you installed the dev package containing the headers (should be x11proto-core-dev I think)? 

If you're building X-based applications you may want to just go ahead and install the whole xorg-dev metapackage rather than picking away at each individual dependency

---

### Post by Tinker Tantrum on 2014-09-20
Excellent. That did the trick. Thank you steeldriver ;)

---

