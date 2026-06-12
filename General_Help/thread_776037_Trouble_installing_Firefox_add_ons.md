---
title: "Trouble installing Firefox add ons"
date: 2008-04-30
forum: General Help
---

### Post by Azrael Strife on 2008-04-30
When attempting to install any of them I get an error, this is from the error console:

Error: installLocation has no properties
Source File: file:///usr/lib/firefox/components/nsExtensionManager.js
Line: 3938

I got this error on Firefox 2, Firefox 3 was removed from my system since it got simply unmanageable.

Has this happened to anyone else? any ideas?

---

### Post by dwarness on 2008-04-30
Delete your ~/.mozilla directory and try again.  Firefox 3 made some setting in there that goofs with things.  After deleting this directory, firefox2 will recreate it with the proper settings it needs.

---

### Post by Azrael Strife on 2008-04-30
Thanks for the fast response, worked like a charm!

---

