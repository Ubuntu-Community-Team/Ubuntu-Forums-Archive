---
title: "compiler problem with breezy"
date: 2005-10-18
forum: General Help
---

### Post by Ugeek on 2005-10-18
This is my first post. 
I upgraded breezy from hoary and had no problem. :) It also correctly configured my monitor(compaq 7500) that hoary could not :D .
 But i had problems with fresh install. Frestly installed it did not find /usr/lib/ctrl.o to run gcc/gfortran. I have used the cd image version. I  had found the same problem with breezy-preview  also. I also checked the MD5SUM to be correct in both cases.

Did any other faced the same? 

My System-celeron-2.6ghz , 512mb  ram, intel 845 chipset

---

### Post by Kyral on 2005-10-18
Stupid question, but did you install build-essential?

---

### Post by Ugeek on 2005-10-22
Thanks, got it right using build-essential. gcc alone did not work.

---

