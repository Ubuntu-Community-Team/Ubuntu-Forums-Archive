---
title: "rsyncing an already rsynce'd directory."
date: 2016-04-14
forum: General Help
---

### Post by biosboy4 on 2016-04-14
rsyncing an already rsynce'd directory. Can/should this be done? What are the repercussions of this? Would I have to restore delta files twice?

Try to respond quickly if possible, I am actively working on the project.

Thanks for all your open source help.

---

### Post by ajgreeny on 2016-04-14
If you rsync a directory to a destination and immediately rsync it a second time to the same destination, the destination will receive nothing as there will have been no changes to the source files.  What delta-transfer are you carrying out?

Perhaps I have totally misunderstood your question, but that is the whole point of rsync (or one of them); that only changed files are copied.

---

