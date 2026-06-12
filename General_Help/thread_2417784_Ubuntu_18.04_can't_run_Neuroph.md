---
title: "Ubuntu 18.04 can't run Neuroph"
date: 2019-04-27
forum: General Help
---

### Post by joesalmon1985 on 2019-04-27
I'm running Ubuntu 18.04 and cannot run Neuroph. I think I'm affected by this bug [https://bugs.launchpad.net/ubuntu/+source/gcc-7/+bug/1764701](https://bugs.launchpad.net/ubuntu/+source/gcc-7/+bug/1764701) as I get the below error message

Inconsistency detected by ld.so: dl-lookup.c: 111: check_match: Assertion `version->filename == NULL || ! _dl_name_match_p (version->filename, map)' failed!


What is odd though is that I ran this program fine before. When it stopped loading I tried to delete it and re install but it still doesn't work.

What commands can I run to provide the information you guys need to help identify what I can do to fix this?

---

