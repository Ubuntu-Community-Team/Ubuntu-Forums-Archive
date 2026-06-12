---
title: "How to start using PostgreSQL using Ubuntu ?"
date: 2019-08-04
forum: General Help
---

### Post by tangara on 2019-08-04
I have just installed a copy of Ubuntu suing Windows Store.

Basically, I followed this tutorial 
[https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-16-04)

When Ubuntu shows the below, I thought I can start using psql but all I get is a bunch of errors

Success. You can now start the database server using:

    /usr/lib/postgresql/10/bin/pg_ctl -D /var/lib/postgresql/10/main -l logfile start

The error are ;

update-alternatives: using /usr/share/postgresql/10/man/man1/postmaster.1.gz to provide /usr/share/man/man1/postmaster.1.gz (postmaster.1.gz) in auto mode
invoke-rc.d: could not determine current runlevel
Setting up postgresql (10+190) ...
Setting up postgresql-contrib (10+190) ...
Processing triggers for ureadahead (0.100.0-21) ...
Processing triggers for systemd (237-3ubuntu10.21) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
tangara@DESKTOP-1KGGO27:~$ sudo -i -u postgres
postgres@DESKTOP-1KGGO27:~$ psql
psql: could not connect to server: No such file or directory
        Is the server running locally and accepting
        connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5433"?
postgres@DESKTOP-1KGGO27:~$ /urs/lib/postgresql/10/pg_ctl -D/var/lib/postgresql/10/main -l logfile start
-bash: /urs/lib/postgresql/10/pg_ctl: No such file or directory

Hope someone tell me what's the problem. 
Tks.

---

### Post by Holger_Gehrke on 2019-08-04
The problem is that you're running on the Windows Subsystem for Linux (WSL). Running Linux programs on WSL is like running Windows programs on Wine: it works mostly, but not always. The psql client is trying to talk to the server using a Unix domain socket. Those are implemented in WSL but not completely. The workaround is to make the client use TCP/IP loopback and the default port 5432.```
psql  -h localhost -p 5432
```
Holger

---

### Post by SeijiSensei on 2019-08-04
Great answer from Holger. I've used PostgreSQL for decades and would never have diagnosed this problem.

```
bash: /urs/lib/postgresql/10/pg_ctl: No such file or directory
```

That error is from misspelling "/usr/" as "/urs/".

---

### Post by tangara on 2019-08-06
Hi Holger,

I tried your method and it gives me psql (10.9 (Ubuntu 10.9-0ubuntu0.18.04.1), server 10.7)
Type "help" for help.

postgres=#

can I know the way to start using psql cos I am not sure what postgres=# is tyring to tell me....

Wish there is a manual how to use psql with Ubuntu WSL....

---

### Post by tangara on 2019-08-06
Hello,

I changed it to usr but then bahs said No such file or directory.

What could be the problem ?

 /usr/lib/postgresql/10/pg_ctl -D/var/lib/postgresql/10/main -l logfile start
-bash: /usr/lib/postgresql/10/pg_ctl: No such file or directory

---

### Post by Holger_Gehrke on 2019-08-06
Once the server runs and the client can connect to it, Postgres on WSL should be the same as on Windows or Linux. What the psql client gives you is a prompt. You're supposed to enter commands now. You might want to take a look at the [documentation for PostgreSQL]("https://www.postgresql.org/docs/10/index.html").

And the "No such file or directory"-error is due to something missing in the path you're giving. According to the [Ubuntu Package search]("https://packages.ubuntu.com/search?searchon=contents&keywords=pg_ctl&mode=exactfilename&suite=bionic&arch=any") 'pg_ctl' is in '/usr/lib/postgresql/10/bin/' on Ubuntu 18.04.

Holger

---

### Post by SeijiSensei on 2019-08-06
Do you know SQL?  The prompt indicates that the client is ready for you to type in SQL commands.

First, though, you should add your username to PostgreSQL and create a database of your own.

```

sudo -u postgres createuser yourusername
sudo -u postgres createdb yourusername

```

Using sudo in this fashion runs the createuser/createdb commands as the user postgres rather than root. Ignore any warnings about not be able to change directories.

Now you should be able to connect to your very own database:
```
psql yourusername
```

You'll get a different prompt, too. The one with the # that you cite above means you're logged in as an administrator. Unless you know what you're doing, that's probably not a good idea.  It's better to have your own database where you can screw up and not have it affect the entire database server.

---

