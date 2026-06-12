---
title: "Postgres Woes: Unable to log in to Postgres"
date: 2016-01-28
forum: General Help
---

### Post by 5-joe-r on 2016-01-28
I want to install the latest Postgresql. I'm on Ubuntu 15.10. I followed the instructions here ([https://help.ubuntu.com/community/PostgreSQL](https://help.ubuntu.com/community/PostgreSQL)), but when I get to this step:

sudo -u postgres psql postgres

it fails, as below:

sudo -u postgres psql postgres
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
job-working-directory: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
could not identify current directory: No such file or directory
psql: could not connect to server: No such file or directory
    Is the server running locally and accepting
    connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?

I've searched and tried several solutions, none of which have worked, including:
 
 - Uninstalling and reinstalling Postgres
 - Trying to access using -U postgres -h localhost (that got me connected, but then Postgres asked for a password, which I don't have. Entering none did not work)
 - Creating a symlilnk: sudo ln -s /tmp/.s.PGSQL.5432 /var/run/postgresql/.s.PGSQL.5432
 - Updating my /etc/postgresql/9.4/main/pg_hba.conf file.

Any help is appreciated.

Thanks!

---

