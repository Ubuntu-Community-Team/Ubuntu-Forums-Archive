---
title: "IE4Linux in a better directory"
date: 2007-10-18
forum: General Help
---

### Post by bone2006 on 2007-10-18
Is there a directory that IE4Linux should be installed on?  When I fire up the terminal and follow these instructions it places it in the home directory, but wondering if placing it in the bin directory or another directory is better than in home?

 wget [http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz](http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz)
 tar zxvf ies4linux-latest.tar.gz
 cd ies4linux-*
 ./ies4linux

---

### Post by bodhi.zazen on 2007-10-18
There is no place like /home

IMO $HOME is best

---

### Post by LanDan on 2007-10-18
not the normal procedure in linux indeed, but then again, its not a linux application.

for ie Home is best, what i personally prefer to rename the /home/user/bin folder to /home/user/.bin

this makes it a hidden file so it doesn't disturb me that much

---

### Post by bone2006 on 2007-10-18
thanks
I'll put it in a hidden directory so that it won't bother me as much either

---

### Post by TimGS on 2007-10-30
For the record I found that changing the directory stopped ie5 and ie5.5 working. 

No probs with ie6 though.

I'm a linux newbie, so don't expect an explanation from this quarter however!

-- Tim

---

### Post by bone2006 on 2007-10-31
I can imagine changing the directory would have an effect on the pointers/shortcuts and the way it's setup, but I did it on a new install.  I'm just using IE6 though and worked just fine.

I created a folder called .IE in home and navigated before running the commands and it worked fine.

One thing is that there's a bin folder in my home now also.  Which is annoying.

---

