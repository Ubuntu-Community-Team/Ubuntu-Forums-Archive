---
title: "Sorting hidden files before other files"
date: 2006-11-29
forum: General Help
---

### Post by justy0 on 2006-11-29
Hi,

I would like ls to output hidden files before other files, but
currently it mixes them ignoring the dot in front. This also
affects the way MC (Midnight Commander) is sorting when Case
Sensitive is turned OFF. I use en_CA locale. I figured that both
'sort' and 'mc' as well as 'ls' are all using information stored
in LC_COLLATE to determine sorting order. I tried to change LC_COLLATE
structure in en_CA file defining locale for en_CA (for other things
as well) but I still don't quite understand the structure for LC_COLLATE.
Can you give me any hints what to do?
I might resort to changing LC_COLLATE to LC_COLLATE="C" which solves
the problem. However, I would rather understand where the problem is
and make appropriate changes to en_CA file (the file located in
/usr/share/i18n/locales)

Thanks

---

