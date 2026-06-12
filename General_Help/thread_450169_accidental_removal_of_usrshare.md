---
title: "accidental removal of /usr/share"
date: 2007-05-21
forum: General Help
---

### Post by valtru on 2007-05-21
is there anyway to recover it?

TIA :(

---

### Post by jazzgossen on 2007-05-21
If you removed it with "sudo rm -r /usr/share" or something like that, I doubt that you can restore it. You can,however, create a new (empty) /usr/share.

I think "sudo mkdir /usr/share" should work. Then, make sure it's readable and executable by all, and writable by root only.

---

