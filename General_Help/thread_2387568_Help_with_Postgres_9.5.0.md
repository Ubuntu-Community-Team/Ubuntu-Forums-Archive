---
title: "Help with Postgres 9.5.0"
date: 2018-03-20
forum: General Help
---

### Post by dagger09 on 2018-03-20
Hey guys, need help with 2 situations.
1. I have installed PostgreSQL 9.5.0 via source. I want to make sure the Postgres server starts on boot and shuts down on before system turns off.
I am using Ubuntu 16.04 LTS.
What scripts do I write and more importantly where should I put them?
I read something about rc.local, but didn't do any good.

2. Since I have installed Postgres via source, the data_directory in postgres.conf is commented. How do I make sure it is pointing to the correct location.
i.e. The entry of `data_directory` should show the correct path of data_directory.


TIA.

---

### Post by SeijiSensei on 2018-03-20
You need to add a line to /etc/rc.local that starts the server using the pg_ctl command.  /etc/rc.local runs with root privileges, but PostgreSQL has to be started as the "postgres" user for security.  I have a server with a self-compiled version of PG installed to the default /usr/local/pgsql directory.  In /etc/rc.local I have the line

```
su -c '/usr/local/pgsql/bin/pg_ctl start -D /usr/local/pgsql/data' postgres
```

That runs pg_ctl as the postgres user and starts the server using the default data directory /usr/local/pgsql/data.  Modify it as needed.

I don't know of a complementary method to shut down the server.  My servers are mostly virtual and rarely shut down.  However the PG server should correctly handle the SIGTERM signal it receives from the Linux kernel during shutdown and close the server gracefully.  See "man postgres" for details.

---

