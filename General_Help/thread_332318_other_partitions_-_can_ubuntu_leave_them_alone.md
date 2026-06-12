---
title: "other partitions - can ubuntu leave them alone"
date: 2007-01-05
forum: General Help
---

### Post by newsman on 2007-01-05
Is there a way to stop ubuntu from checking other partitions (that are ext3) at load up time 


they belong to other OSes and everytime i load to them and then load back, ubuntu gives an error on them although they are clean (i think ubuntu tries to write to those partitions for which it does not have permission for and hence the error)

thus i want to stop this error at load time...

---

### Post by meng on 2007-01-05
You could change the entries for those partitions in the /etc/fstab so the last 2 numbers are 0 0, I think this should do the trick.

---

### Post by newsman on 2007-01-05
arigatou ne,,,,

worked on ubuntu and worked on other OS trying to spoil ubuntu as well....

(also appreciate the quick reply as well, thanks a lot)

---

