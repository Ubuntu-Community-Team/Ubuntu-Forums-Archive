---
title: "postgresql initdb"
date: 2008-02-12
forum: General Help
---

### Post by David G Oliver on 2008-02-12
I've got gutsy gibbon 7.10 on a server and on a laptop (Xubuntu) and I can't get postgresql's initdb to work with either one.  bash says the command can't be found, but all postgresql references tell me to use this to set up a new database cluster where I want it...  can anyone help?

---

### Post by _chimp on 2008-02-14
I assume that you have tried /usr/local/pgsql/bin/initdb, as this is what all of the standard documents seem to say?
However of course there is no bin directory within /usr/local/pgsql so it doesnt work...

I have just been doing the same things as you and getting postgres up and running on another computer.  The last time I got fed up with the lack of ubuntu specific documentation and compiled it from source.  However the answer is simple (after a lot of searching) -

/usr/lib/postgresql/8.2/bin/initdb 

will get your database up and running.

/usr/lib/postgresql/8.2/bin/initdb -D /usr/local/pgsql/data
will bring ubuntu back into line along with the rest of the documentation.
Good luck :)

<edit>
I guess that just in case you didnt work it out -
if the manual asks for /usr/local/pgsql/bin/createuser then you use
/usr/lib/postgresql/8.2/bin/createuser
and so on for the other createdb, psql and other bits.

---

### Post by David G Oliver on 2008-02-15
Thanks very much.  I had roamed around in 
/etc/postgresql/8.2
but did not find initdb.  I will have to hone my searching skills (I am newish to Linux, if not to computing).

I have my database up and running thanks to you!

---

