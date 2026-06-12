---
title: "exit info command"
date: 2016-11-10
forum: General Help
---

### Post by AttentionDesperate on 2016-11-10
how to exit info command

like 

sudo info shutdown

---

### Post by deadflowr on 2016-11-10
Try 'q'

Edit: Is there any reason to use sudo?

---

### Post by AttentionDesperate on 2016-11-10
my lack of knowledge of when sudo is necessary or not

---

### Post by kingneutron on 2016-12-02
Sudo is only necessary if you need admin rights to do commands that generally involve system administration.  Things like fdisk, hdparm, mkfs, grub, and changing file permissions usually involve sudo.  Getting "info" or "man" information on a command can be done without root permissions. FYI

---

