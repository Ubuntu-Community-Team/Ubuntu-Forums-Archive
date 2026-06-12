---
title: "sqlite3"
date: 2021-12-23
forum: General Help
---

### Post by box02-0 on 2021-12-23
Hi.

                                           I installed sqlite3, but when I request the version number, I get:

sqlite3 -version
-- Loading resources from /home/mg/.sqliterc
Error: near line 4: near "*": syntax error
3.31.1 2020-01-27 19:55:54 3bfa9cc97da10598521b342961df8f5f68c7388fa117345eeb516eaa837balt1

What to do here?

Thanks,
M...

---

### Post by oldfred on 2021-12-23
I get same version 3.31 in my Kubuntu 20.04, but do not have these two lines?
Are you loading from some other application?

-- Loading resources from /home/mg/.sqliterc
Error: near line 4: near "*": syntax error

---

### Post by vanadium on 2021-12-26
".sqliterc" is a hidden file that contains some command automatically executed when launching, i.e. you can set some different defaults there. Open and inspect the contents. Alternatively, it will be safe to delete that file. If you do not know about that file, you probably don' t need it in the first place.

---

