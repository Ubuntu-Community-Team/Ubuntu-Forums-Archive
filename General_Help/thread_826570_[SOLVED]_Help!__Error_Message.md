---
title: "[SOLVED] Help!  Error Message"
date: 2008-06-12
forum: General Help
---

### Post by mpschenck on 2008-06-12
How do I fix this...

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

btw: I'm know practically nothing about Ubuntu.
Any help would be appreciated.

---

### Post by lisati on 2008-06-12
From a terminal (you can get to it from the Applications->Accessories menu) type in ```
sudo dpkg --configure -a
``` and press 'Enter'. You'll be asked for your password - don't be alarmed if it doesn't show, it will still be accepted.

---

### Post by mpschenck on 2008-06-12
Thanks, Dude!  It worked.

---

