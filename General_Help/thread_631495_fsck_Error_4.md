---
title: "fsck Error 4"
date: 2007-12-04
forum: General Help
---

### Post by alex.de on 2007-12-04
Hi, after using Gutsy for 1 and a half month, everything was running fine. Since today, it does a fsck, which is completely normal (after 30 boots) and at around 35%, it shoots all sorts of error, including error 4. After a few minutes, I now have access to the terminal but I cant do anything because it's in a read-only mode.

After running fsck again in the terminal, I get spammed with the same error:

```
exception Emask 0x0 SAct 0x0 Serr 0x0 action 0x0
(BMDHA stat 0x25)
cmd c8/00:f8:17:11:78/00:00:00:00:00/e2 tag 0 cdb 0x0 da

```

after that being spammed around 10 times (about 10 seconds interval for each) ,a get approximitely 10 lines saying:

```
I/O error on device sda1, logical block 51779xx (xx is just a number that gets incremented)
```

I really need help for this please. Thank you.

---

### Post by Herman on 2007-12-07
[                      Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem")

---

