---
title: "Database Apps"
date: 2006-11-24
forum: General Help
---

### Post by ColinG on 2006-11-24
Open Office database does not work on my Kubuntu or Ubuntu install. This is a problem shared by others and is a bug somewhere.

As an alternative I have looked at Glom and Knoda but when I try and run them I get asked for a password and user name. I use those attributable to my Kubuntu log-in but I then get the response that the database front end cannot connect to the server. At this stage I am completely lost and all I need is a database that works much like Open Office/Access.

Is there a kind soul out there who could help me out?

Many thanks

---

### Post by reclusivemonkey on 2006-11-26
> **ColinG said:**
> Open Office database does not work on my Kubuntu or Ubuntu install. This is a problem shared by others and is a bug somewhere.

As an alternative I have looked at Glom and Knoda but when I try and run them I get asked for a password and user name. I use those attributable to my Kubuntu log-in but I then get the response that the database front end cannot connect to the server. At this stage I am completely lost and all I need is a database that works much like Open Office/Access.


I doubt you are going to get anything that works/looks like Access in Linux. Open Office Database seems to work OK here on Edgy. I just created a quick test DB, so I didn't use it thoroughly; what is the problem you are having?

What sort of DB development are you planning?

---

### Post by Marsolin on 2006-11-26
I haven't tried it myself, but [Kexi]("http://linuxappfinder.com/package/kexi") is supposed to be a good database program.

---

### Post by JackRazz on 2006-11-27
In Ubuntu Edgy, Kexi doesn't work with PostgreSQL.  I think it may be because PostgreSQL is in the Universe instead of the Main repository.  Thus, the PostgreSQL support lib's were excluded.  If anyone has Kexi with PostgreSQL working in Ubuntu, I'd like to hear.  I suppose I could try compiling from source.

Otherwise, it starts up fine, is easy to use, and looks like an good [replacement]("http://www.tuxmagazine.com/node/1000207") for MS Access.  It's still a bit new and missing some important features.

JackRazz

---

### Post by ColinG on 2006-11-27
> **ColinG said:**
> Open Office database does not work on my Kubuntu or Ubuntu install. This is a problem shared by others and is a bug somewhere.

As an alternative I have looked at Glom and Knoda but when I try and run them I get asked for a password and user name. I use those attributable to my Kubuntu log-in but I then get the response that the database front end cannot connect to the server. At this stage I am completely lost and all I need is a database that works much like Open Office/Access.

Is there a kind soul out there who could help me out?

Many thanks

OOo Base's forms wizaed does not work, it gets through to where I click on finish and then it just hangs. I am not the only one to report this. It worked ok when I tried FC6 and is also fine on Mandriva 2007. Not every Ubuntu Edgy user gets this problem but others have posted about it on these forums. 

My database requirements are small, and I could even get away with the likes of Tellico (although I must emphasise "get- away"). I just have a need for small local databases that are kept solely on my hard drive. That said, Glome did look to be a nicely put together app, its in the repos if only I could find out how it works!!

Kexi, which is not part of this topic really, has no report generation yet so it is a no no.

---

### Post by JackRazz on 2006-11-27
Check out Knoda. It has reporting features.

---

### Post by ColinG on 2006-11-27
I tried Knoda but like Glome it asks for a user name and password to access the db server. At that point I am lost as I know nothing about these. :confused:

---

### Post by JackRazz on 2006-11-27
Colin,
I'm not that familiar with MySQL as I'm using PostgreSQL.  I used this [PostgreSQL Quickstart]("https://help.ubuntu.com/community/PostgreSQL?highlight=(postgre)").  I did the Installation and Basic Server Setup steps only.

I had problems with PostgreSQL starting up correctly after rebooting. So I  turned off the Database Server from automatically staring up from System/Administration/Services item in the menus  and then setup a launcher to start PostgreSQL with ```
gksu /etc/init.d/postgresql-8.1 start
```

In order for knoda to recognize PostgreSQL you also need to install *libhk-classes-postgres*.  Then log into the PostgreSQL server with knoda via:
```

Host:                        localhost
Database name:        MySQL (or whatever you created)
User:                        postgres
Password:                  whatever you set
TCP Port:                   5432
```

I you want to try this and have problems, let me know.  I would imagine you  could find a quickstart for MySQL and it should be similar.

JackRazz

---

