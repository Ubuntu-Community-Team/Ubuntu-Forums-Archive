---
title: "Question regarding commands in Terminal."
date: 2008-07-09
forum: General Help
---

### Post by MasterNetra on 2008-07-09
I was wondering if there is "Wild Card" command that like in windows that tells the system to do stuff to multiple files. Let me give a example of what i'm talking about.

3 files: Afile.txt, Abfile.txt, Bfile.txt

What i want to do is say copy Afile and Abfile without having to copy both individually something like;

cp A*.txt /home/user/crapfiles/

---

### Post by bodhi.zazen on 2008-07-09
Yes, there are several.

Everything from * to ? to regular expressions.

cp *.txt

cp {A,B,C}file.txt

cp ?file.txt

Best do some reading :

[http://linuxcommand.org/](http://linuxcommand.org/)

Or search on man bash.

---

### Post by MasterNetra on 2008-07-09
k thanks

---

