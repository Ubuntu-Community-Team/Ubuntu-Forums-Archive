---
title: "postgresql"
date: 2005-08-14
forum: General Help
---

### Post by fractalvibes on 2005-08-14
I just got the postgresql and postgresql-client packages via synaptic - I'm using the KDE desktop and don't see anything in the menus now - tried to instantiate via terminal - no dice.  Ditto for MySQL.  When I reboot the machine I can indeed see both services starting up.  Are some more packages need for both?

thanks,

fv

---

### Post by DJ_Max on 2005-08-14
What are you trying to do? How did you try to inititate them?

---

### Post by fractalvibes on 2005-08-14
I tried a number of things from the command line

postgres
postgresql
postgresql-client
postmaster

all which returned "command not found".
Also got postgresql-docs via synaptic and would like to have a read.  Postgres looks like a very interesing RDBMS from what little I've read about it...

fv

---

### Post by DJ_Max on 2005-08-14
Yea, Postgresql is my DB of choice. As far as the binaries Ubuntu has, I'm not sure about the problem you're having, as I've installed PgSQL from source.
There are tools like pg_ctl and such.

Try psql

---

### Post by sreid on 2005-08-14
Try "psql" from the command line. That'll give you the standard command-based interface. You might want to install pgadmin3 if you're new to PostgreSQL, as it provides a GUI interface.

More generally speaking, you can use "dpkg -L [packagename]" to see what files a package has installed. From that list you can find the executable to run, as well as any documentation it has installed.

---

### Post by fractalvibes on 2005-08-14
OK - may be on the right track here.

psql on the command line responds:

psql (pg-wrapper) : no database specified

So something was invoked.  No database has been defined yet, so of course none could be specified.

Progress.  So is postgres several cuts above MySQL?  I use DB2 UDB 8 hours a day on the job and like the feature set.   

fv

---

### Post by DJ_Max on 2005-08-14
MySQL 5 is not just gaining features other RDBMS have already had.
Take a look here [http://www.postgresql.org/docs/8.0/static/installation.html](http://www.postgresql.org/docs/8.0/static/installation.html) for initializing the DB, and creating users and such.

I haven't used a GUI, it may be worth looing into for a desktop solution.

---

### Post by fractalvibes on 2005-08-14
Many thanks, DJ!  All of my current hosting solutions are still using MySQL 4.x.x, so even things like subselects are not available.  Looking forward to seeing Postgres - seems like it has some of the same advanced functionality as DB2.

fv

---

