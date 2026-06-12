---
title: "Backup using remastersys"
date: 2015-04-29
forum: General Help
---

### Post by ARUN_V_R on 2015-04-29
I installed dspace 4.2 on ubuntu 12.04. I also installed remastersys to make a live iso image. But it failed to take backup and says the compressed file system is larger than the iso9660 specification allows for a single file. How to get rid of this?? Is there any files to delete in filesystem?? Pls help me.

---

### Post by sandyd on 2015-04-29
remastersys has a 4GB limitation.

If you want to backup more than 4GB, use a backup tool such as clonezilla to create an image of your installation.

---

### Post by ARUN_V_R on 2015-04-30
No it can be done with remastersys by deleting the unwanted files. But i don't know which of them are these files.

---

