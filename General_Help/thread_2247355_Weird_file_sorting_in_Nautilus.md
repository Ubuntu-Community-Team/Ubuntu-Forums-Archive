---
title: "Weird file sorting in Nautilus"
date: 2014-10-07
forum: General Help
---

### Post by dewdrop_world on 2014-10-07
If I do *ls -1 ~/share*, part of the output is:

SC
sc3.6.git
sc3-plugins
sc-hjh.git

In Nautilus, I get:

sc3.6.git
sc3-plugins
SC
sc-hjh.git

Why? Even in a case-insensitive sort, "sc" < "sc3.6.git" simply because it's shorter -- I'm not quite grasping the reason why numbered file or directory names must come before those lacking numbers.

hjh

---

