---
title: "How to converting file system from one into another ?"
date: 2005-04-05
forum: General Help
---

### Post by cyu021 on 2005-04-05
Hi folks,

I am trying to find a command that is capable of converting my file system from EXT3 to RESEIFS.

Is there such a command exist? or there are some other alternative ways of doing what I want to achieve?


Thanks in advance,
James

---

### Post by lao_V on 2005-04-05
You can use [mkreiserfs]("http://gd.tuwien.ac.at/linuxcommand.org/man_pages/mkreiserfs8.html") command

---

### Post by alastair on 2005-04-05
As far as I know, you cannot convert from one to another leaving your data intact (except for ext2 -> ext3). So you will need to BACKUP your system, then reformat (mkfs).

---

