---
title: "how to uninstall?"
date: 2005-07-05
forum: General Help
---

### Post by kimes on 2005-07-05
How can I uninstall some programs which is intalled by './configure and make' way..?
And is there any ways to know what the above way installation installed on my machine?
I think .deb way is much better :)

---

### Post by SGC on 2005-07-05
If you still have the files, do the following:
sudo make uninstall

If you want to create .deb package from programms that compile with ./configure, make:
then install **checkinstall** with apt-get and then replace **make install** with **checkinstall -D make install** that will create a .deb package that you can uninstall it later if you want

---

