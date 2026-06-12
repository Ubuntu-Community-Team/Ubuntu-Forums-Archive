---
title: "Scripts in /usr/lib/systemd/system-sleep ignored"
date: 2017-08-14
forum: General Help
---

### Post by dmk1 on 2017-08-14
Hi

I've noticed, that scripts placed in /lib/systemd/system-sleep are run on suspend and getting from it, but not those from /usr/lib/systemd/system-sleep. The later is not mentioned in the systemd manual, however I've found a lot of mentions about that possibility, and since it's also an existing directory I thought that I may put it there as well. The script, I've tested it on, is owned by root and marked as executable. What am I doing wrong? :confused:

The system is Xubuntu 17.04

Thank you!

---

