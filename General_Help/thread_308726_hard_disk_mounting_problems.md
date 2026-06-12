---
title: "hard disk mounting problems"
date: 2006-11-28
forum: General Help
---

### Post by kelxso on 2006-11-28
for some reason i cant access my shared harddrives on my system it
error: device /dev/hdd1 is not removable

error: could not execute pmount
could someone explain why this happens

---

### Post by PriceChild on 2006-12-01
*thread moved*

---

### Post by nixclusive on 2006-12-01
pmount is a wrapper script over mount that allows normal users to mount/umount removable media. In the default Ubuntu installations, mount is already set setuid... use 'mount' instead.

---

