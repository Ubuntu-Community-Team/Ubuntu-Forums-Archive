---
title: "need some help"
date: 2007-08-08
forum: General Help
---

### Post by devin0 on 2007-08-08
Whenever I go to update my system, weather it is through the terminal, the update manager, or add/remove applications, I keep getting this error message-
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

can someone please tell me how to fix this problem?

---

### Post by Gremlinzzz on 2007-08-08
sudo apt-get -f install

---

### Post by devin0 on 2007-08-08
i did that, and got the same error message

---

### Post by Dark Star on 2007-08-08
Do this```
 sudo dpkg --configure -a
``` then after the process finished do this```
 sudo apt-get install -f
``` This will recover/ fix the error :):guitar:

---

### Post by devin0 on 2007-08-08
thank you so much :)

---

