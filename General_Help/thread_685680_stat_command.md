---
title: "stat command"
date: 2008-02-02
forum: General Help
---

### Post by browning_man9 on 2008-02-02
Hello. I'm attempting to use the stat command to get at the last modification time of a file since the epoch. The manual says that the "valid format sequence" for this is %Y. My question is what is the proper syntax. It's not like "stat -%Y file.txt." I'm using it to write a shell script to compare modification times. I thank you for your help!

---

### Post by browning_man9 on 2008-02-02
any ideas?

---

### Post by Nythain on 2008-02-02
hmmm... just realized it didnt take my original reply... try
stat --format=%Y whatever.txt
that might do the trick,

---

