---
title: "Creating ln Shortcut"
date: 2007-07-22
forum: General Help
---

### Post by Naatan on 2007-07-22
Hi, I just created a shortcut with the following command:

ln -sf ~/DCMS/ /svn/local_projects/DCMS/

Now DCMS is supposed to link to /svn/local_projects/DCMS/, but when I go to DCMS (cd ~/DCMS/) I just end up in the DCMS folder that is supposed to be linked..

Am I doing something wrong?

---

### Post by bodhi.zazen on 2007-07-22
ln -s <existing directory> <link>

So ....

sudo ln -s /svn/local_projects/DCMS/ ~/DCMS

---

### Post by Naatan on 2007-07-22
Ahh I switched them around ^_^ Thanks mate!

---

