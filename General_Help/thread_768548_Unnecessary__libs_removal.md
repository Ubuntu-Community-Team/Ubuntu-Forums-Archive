---
title: "Unnecessary  libs removal"
date: 2008-04-26
forum: General Help
---

### Post by DToNAToR on 2008-04-26
Hi, I was going to clean up my installation a bit and wanted to know how to remove unnecessary libs. The problem is that those were installed manually to compile programs and therefore I can't really follow them now.
I thought of trying to examine all the binaries in the system, and their dynamic linking, then assigning the lib files to packages in the system, excluding them from the big package list and giving me the rest.

Someone knows of an already written tool that does something like this?

---

### Post by ysangkok on 2011-05-19
You could try getting the "atime" (access time) of all files and then sorting them. It's only a clue though. But most manually installed binaries should reside in /usr/local so it should be easy to find them.

If you're looking for packages use debfoster and/or deborphan.

---

