---
title: "when will devIL 1.6.7-5 be in the repo?"
date: 2006-08-02
forum: General Help
---

### Post by themoebius on 2006-08-02
There are a few bugs with devIL 1.6.7-4 (the latest version in the repository), which were fixed in 1.6.7-5 (at least with debian?) back in May. the bug report explaining it: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=314829](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=314829)

When will we see the new package in the ubuntu repositories? I don't like installing packages manually because it complicates things often breaks updating, etc.

---

### Post by soul_rebel on 2006-08-02
You should check the bug reporting tool to see if there is any bug opened for that package. If not you can post one. Reporting bugs sometimes solves the problems, :)
The forum is not the place for this, because few developers read the forums regularly.

---

### Post by soul_rebel on 2006-08-02
double post removed, sorry

---

### Post by themoebius on 2006-08-05
OK, it seems that version 1.6.7-5 is in the edgy repos, but I've heard that upgrading to edgy packages is really dangerous. I looked into getting just libdevil, but it depends on a newer version of libc6, which depends on a newer version of locales. Since these are all packages so crucial to the system, I don't think its safe to upgrade to edgy versions based on what people said in IRC. What are my alternatives since I need to get this newer version of libdevil for my development work?

---

