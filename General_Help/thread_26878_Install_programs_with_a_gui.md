---
title: "Install programs with a gui?"
date: 2005-04-14
forum: General Help
---

### Post by Mytos on 2005-04-14
Is there some kind of program to install stuff you downloaded instead of using the terminal?

I can install some stuff with synaptics, but is there no way to install files you downloaded yourself?



/Linux Newbie

---

### Post by Leif on 2005-04-14
A few programs have GUI installers, but for the most part, no.

---

### Post by Mytos on 2005-04-14
Ok

well, what was it that you type to install programs?

Lets say you have a  .deb file in the home folder that you want to install
and how is it with .tar and gz files, do you have to unzip them first?

---

### Post by Mytos on 2005-04-14
Ok

well, what was it that you type to install programs?

Lets say you have a  .deb file in the home folder that you want to install
and how is it with .tar and gz files, do you have to unzip them first?

Thanks in advance

---

### Post by Leif on 2005-04-14
with a deb file, you do "sudo dpkg -i file.deb". 

with a tar.gz file, you would normally "tar xzvf file.tar.gz", then cd to the directory it was extracted to, "make && make install". this is NOT a rule, however, and you should read whatever documentation was included with the package, normally in a file called Readme or Install.

---

### Post by Mytos on 2005-04-14
ok thanks  :-)

---

