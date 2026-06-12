---
title: "Python Eric 6 IDE unable to launch Qt designer"
date: 2019-09-10
forum: General Help
---

### Post by hayat-jk on 2019-09-10
I have installed eric6 on top of Ubuntu 16.04, I launched it and created a new project, I added a new form but the qt design editor did not open.

I read many articles and searched the web, all what I've found that eric6 tool comes with qt designer builtin, and when click on any .UI file the designer editor should open, but unfortunately I'm unable to launch ..

Any help will be highly appreciated,
Thanks, 
hayat

---

### Post by mörgæs on 2019-09-11
Hi, welcome to the fora.

Please copy ```
apt list --installed | grep -i 'qt5'
``` and paste it to the command line, run it and post the results in CODE tags.

---

