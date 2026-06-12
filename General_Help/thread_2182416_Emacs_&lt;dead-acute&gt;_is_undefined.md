---
title: "Emacs: &lt;dead-acute&gt; is undefined"
date: 2013-10-21
forum: General Help
---

### Post by sverrirkr on 2013-10-21
All other dead keys are working properly. Using an Icelandic keyboard layout.

How do I fix this?

---------

Ubuntu 13.10 as guest on VMware.

---

### Post by sverrirkr on 2013-10-22
Solved.

Add (require 'iso-transl) to .emacs file.

---

### Post by buisteric on 2013-10-26
I had the same problem, added the iso-transl, but that solved things only partially. I still cannot enter a ç, ´, ` and ^.

---

