---
title: "Connecting with other user to Postgres"
date: 2005-05-25
forum: General Help
---

### Post by xhantt on 2005-05-25
Hi, I'm wandering how to connect to postgres using other user than the login:

As postgres user I issue the following commands:

createuser -ADP nouser
createuser -O nouser nouser

Till here everithing went OK, Now as may login user I do

psql -U nouser -W nouser

After enter the password I get

psql: FATAL:  IDENT authentication failed for user "nouser"

---

### Post by amerigo5 on 2006-08-27
I am having the same issue after installing 8.1 on a fresh install of 6.06.1.  Can anyone give a step by step instructions on making an account (other than postgres) connect to the database? Thanks.

---

### Post by Nickb-k on 2006-10-31
Hi, well I am also having these issues.  Could you post your pg_hba.conf file here, and we can compare notes:

```

# TYPE  DATABASE    USER        CIDR-ADDRESS          METHOD

# "local" is for Unix domain socket connections only
local   all         all                               password

# IPv4 local connections:
host    all         all         127.0.0.1/32          trust

# IPv6 local connections:
host    all         all         ::1/128               trust
host    all         all         10.0.0.0/16           trust

```

I have tried various combinations of this file, including having the first entry set to trust.

I can only log onto the postgres server with users ```
postgres[/postgres] and [code]nick
```. (nick is also a unix account name.

---

### Post by Nickb-k on 2006-10-31
Ok, the problem for me was that postgres was reading from a different config file.  To check for this problem, do as follows:

```


#  sudo updatedb
#  locate pg_hba.conf


```

For me, this returned two directoruies:

```
/etc/postgresql/8.1/main/pg_hba.conf
/usr/local/pgsql/data/pg_hba.conf
```

Now, delete the rogue config file:

```


#  cd /etc/postgresql/8.1/main/
#  rm pg_hba.conf

```

Now create a symlink (or alternatively copy the config file into /etc/postgresql/8.1/main/)

```

# ln -s /usr/local/pgsql/data/pg_hba.conf pg_hba.conf

```

now restart postgres:

```


# sudo  /etc/init.d/postgresql-8.1 restart


```

Be happy! :)

---

