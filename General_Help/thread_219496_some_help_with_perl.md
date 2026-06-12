---
title: "some help with perl"
date: 2006-07-20
forum: General Help
---

### Post by lex1 on 2006-07-20
i have to folow this paragraph(see below) before installing perl script.
there a few points i need to clear up.



be sure you have perl5.003 or later, installed with
the DB_File  module.  Don't forget to run h2ph when installing
 perl(cd /usr/include; h2ph *.h sys/*.h).  If you don't have
 DB_File, get db from ftp.cs.berkeley.edu:/ucb/4bsd/db.1.85.tar.gz,
install it, and  then reinstall perl so that the DB_File module is
>available.--------------------------------------

 a)in dapper perl and h2ph are present how can i chech if this line is present
h2ph *.h sys/*.h)

b) i have downloaded db.1.85 would it be a case of 
tar xvzf db.1.85.tar.gz
cd db.1.85
./configure
make
sudo make install


lex1

---

