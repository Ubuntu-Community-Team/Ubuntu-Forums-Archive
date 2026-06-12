---
title: "avg.deb install problems"
date: 2007-02-18
forum: General Help
---

### Post by bilbobagins on 2007-02-18
Hi have just downloaded avg (avg75lms-r39-a0859.i386.deb) after aborting the rpm download as one of firefox plug in was reading it as a sound file. anyway the file downloaded .deb installer installed it but cant find it on pull downs.I did read how to this somewhere but have lost its location can anyone help me.

---

### Post by Maestro23 on 2007-02-18
If the .deb installed correctly, one why to find out where the .bin is:

Open a terminal:

> whereis <program name>

or

dpkg -L <filename>



---

### Post by mcduck on 2007-02-18
'which appname' will give path to the executable file of program called 'appfile'

for example 'which firefox' returns '/usr/bin/firefox'

---

