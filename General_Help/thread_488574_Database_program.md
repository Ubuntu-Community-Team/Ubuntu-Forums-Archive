---
title: "Database program"
date: 2007-06-30
forum: General Help
---

### Post by ronbrooks on 2007-06-30
I would like to learn more about database programs.  I can't seam to get open office database to work right so is there any other program that I can use. 

Are there any in the Synaptic, and if there is what packages do I need to download.  What is good for someone to start  and learn.  Are there any good how to out there to help with this. 

Thanks

---

### Post by swisscow on 2007-06-30
Try Kexi - its in synaptic

---

### Post by ronbrooks on 2007-06-30
Thanks I will try that now and if anyone else has a suggestion let me know.

---

### Post by ashwin_cse on 2007-06-30
By database programs are you meaning databases or programs that operate over them. In case it was database software, you might try mysql or postgresql, SQLite .

---

### Post by ronbrooks on 2007-06-30
I was referring to a program to set up the database and get it working.

---

### Post by frazelle09 on 2007-07-01
i've been trying to do the same for almost a year for Postgresql and about the most robust one i've found so far is Glom.  i haven't been able to use it very much, but it looks like it can set up the database pretty well and very similar to MSAccess in this respect.

i don't remember how strong a Report generator it has but i understand that OOo is building a better mousetrap, i mean, Report generator, for it's db module.  i suspect that once you have your db setup, you could use a (connector?, i don't remember what it's called) but a program which connects between OOo Base and your db in Postgresql and from there you might be able to generate the reports.

The other programs available and which are more robust are all costly proprietary ones.

Hope this helps.

Have a great evening!  :)

---

### Post by cwaldbieser on 2007-07-01
> **frazelle09 said:**
> i've been trying to do the same for almost a year for Postgresql and about the most robust one i've found so far is Glom.  i haven't been able to use it very much, but it looks like it can set up the database pretty well and very similar to MSAccess in this respect.

i don't remember how strong a Report generator it has but i understand that OOo is building a better mousetrap, i mean, Report generator, for it's db module.  i suspect that once you have your db setup, you could use a (connector?, i don't remember what it's called) but a program which connects between OOo Base and your db in Postgresql and from there you might be able to generate the reports.

The other programs available and which are more robust are all costly proprietary ones.

Hope this helps.

Have a great evening!  :)

Something like knoda ([http://www.knoda.org/]("http://www.knoda.org/")) may be useful.  It is in the repositories.

---

### Post by x1a4 on 2007-07-01
Hi,

I use [PostgreSQL](http://www.postgresql.org/) (db engine) and [pgAdmin](http://www.pgadmin.org/) (pgsql gui).  pgAccess is also a decent PostgreSQL GUI--though pgAdmin is better (IMHO).  

If you want to use [MySQL](http://www.mysql.com/) for a DB engine check out [MySQL GUI Tools](http://dev.mysql.com/downloads/gui-tools/5.0.html/).  

I use pgAdmin when I want to make changes in a hurry and/or don't feel like RTFM'ing.  Otherwise I access pgsql from the command line using Kuake--loads of fun.  :)

---

### Post by milton1 on 2007-07-01
It may also be helpful for you to learn how to use the database without a gui. There are some great tutorials out there to help you get started.

[http://www.w3schools.com/sql/default.asp](http://www.w3schools.com/sql/default.asp)

---

### Post by x1a4 on 2007-07-01
One of the beautiful things about PostgreSQL is that it allows you to easily create databases on the fly.

---

### Post by frazelle09 on 2007-07-01
i did a lot of "resarch" on the net and found postgresql to be the most robust of the free db programs out there.  However all i want to do is just make one pretty simple db.  The real heart of this thing are all the reports we need.  We only have maybe 3 - 4 input forms.

i made one up in Access about 8 years ago where i work and sure it fails every once in a while, but we just restart it and it goes.  About 14 of us work with it at a time.  i don't have the time to learn pg programming and our bosses are going to shell out $80,000 for a professionaly made one which will cost us another $20,000 (is this correct?) a year for maint.  i was hoping to be able to find a good enough front end for pg to do it myself and save the taxpayers a bunch, but neither OOo Base is ready, nor are there any other gui as ready and robust as Access that i'm capable of working with.  Sigh.

Have a great afternoon!  :)

---

### Post by ronbrooks on 2007-07-04
Thanks for all the help and I decided to use Kexi and downloaded it.  I found that it was very easy to use and I followed the tutural on it from start to finish.  As a beginner I have a long way to go but I am having fun just doing it. I looked around the net to see if anyone had some make programs for the program but couldn't find any.  My though was to see what someone else has done and maybe learn from looking at there database program.

I will just have to try defferant thing and see if they will work out. 

Thanks again for the help.

---

### Post by ukripper on 2007-07-04
> **frazelle09 said:**
> i did a lot of "resarch" on the net and found postgresql to be the most robust of the free db programs out there.  However all i want to do is just make one pretty simple db.  The real heart of this thing are all the reports we need.  We only have maybe 3 - 4 input forms.

i made one up in Access about 8 years ago where i work and sure it fails every once in a while, but we just restart it and it goes.  About 14 of us work with it at a time.  i don't have the time to learn pg programming and our bosses are going to shell out $80,000 for a professionaly made one which will cost us another $20,000 (is this correct?) a year for maint.  i was hoping to be able to find a good enough front end for pg to do it myself and save the taxpayers a bunch, but neither OOo Base is ready, nor are there any other gui as ready and robust as Access that i'm capable of working with.  Sigh.

Have a great afternoon!  :)

 if postgresql is that robust  then why we have  stack as LAMP not LAPP?

---

