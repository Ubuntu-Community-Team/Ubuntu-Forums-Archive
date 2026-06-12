---
title: "Postgresql unmet dependencies"
date: 2015-05-09
forum: General Help
---

### Post by l-l-pajuelo on 2015-05-09
I'm using Ubuntu 14.04.2 LTS and I tried to install PostgreSQL using the Ubuntu Software Center and got this error message:
> Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time




The details from the internal error lists so many dependencies that the list is truncated [...] it does not list which dependency is the probelm.

It tags it as a duplicate of ```
https://bugs.launchpad.net/bugs/1097946
```

Though that seems to be a generic install problem bug not specific to PostgreSQL

DuplicateSignature
> software-center:trans-failed:error-dep-resolution-failed

I tried using apt-get
```
sudo apt-get install postgresql postgresql-contrib
```

But got this error
```
Some packages could not be installed. This may mean that you haverequested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 postgresql : Depends: postgresql-9.3 but it is not going to be installed
 postgresql-contrib : Depends: postgresql-contrib-9.3 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.



```

I followed the directions in [https://wiki.postgresql.org/wiki/Apt](https://wiki.postgresql.org/wiki/Apt) ```
sudo apt-get install wget ca-certificateswget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install postgresql-9.4 pgadmin3
```

but got this:
```
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 postgresql-9.4 : Depends: postgresql-client-9.4
                  Depends: postgresql-common (>= 142~) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.



```

So, how do I find out which packages are broken? 
Which dependencies are causing the issue?
Any other way to install PostgreSQL?

---

### Post by dino99 on 2015-05-10
The rule is: follow ubuntu's wiki; everything else can (and often do) met version conflicts.

[https://help.ubuntu.com/community/PostgreSQL](https://help.ubuntu.com/community/PostgreSQL)

So purge the broken installation first: > sudo apt-get purge postgr* > sudo apt-get autoremove  then install 'synaptic': > sudo apt-get install synaptic > sudo apt-get update and install postgresql from there

---

### Post by l-l-pajuelo on 2015-05-10
I purged, installed synaptic and tried to do the installation from there got:
```
E: postgresql-common: subprocess installed post-installation script returned error exit status 127E: postgresql-9.4: dependency problems - leaving unconfigured
E: postgresql: dependency problems - leaving unconfigured
```

Changes applied window had ```
A package failed to install.  Trying to recover:Setting up postgresql-common (166.pgdg14.04+1) ...
/var/lib/dpkg/info/postgresql-common.postinst: 114: /var/lib/dpkg/info/postgresql-common.postinst: adduser: not found
dpkg: error processing package postgresql-common (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of postgresql-9.4:
 postgresql-9.4 depends on postgresql-common (>= 142~); however:
  Package postgresql-common is not configured yet.


dpkg: error processing package postgresql-9.4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postgresql:
 postgresql depends on postgresql-9.4; however:
  Package postgresql-9.4 is not configured yet.


dpkg: error processing package postgresql (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 postgresql-common
 postgresql-9.4
 postgresql
```

I purged/autoremoved again and tried to install following the wiki instructions got this in terminal 
```
Creating config file /etc/postgresql-common/createcluster.conf with new version


Creating config file /etc/logrotate.d/postgresql-common with new version
Building PostgreSQL dictionaries from installed myspell/hunspell packages...
  en_au
  en_gb
  en_us
  en_za
Removing obsolete dictionary files:
 * No PostgreSQL clusters exist; see "man pg_createcluster"
Processing triggers for ureadahead (0.100.0-16) ...
Setting up postgresql-9.4 (9.4.1-1.pgdg14.04+1) ...
Creating new cluster 9.4/main ...
  config /etc/postgresql/9.4/main
  data   /var/lib/postgresql/9.4/main
  locale en_US.UTF-8
Flags of /var/lib/postgresql/9.4/main set as -------------e-C
sh: 1: cannot create /dev/null: Permission denied
[...]
sh: 1: cannot create /dev/null: Permission denied
child process exited with exit code 2
initdb: removing contents of data directory "/var/lib/postgresql/9.4/main"
Error: initdb failed
Error: could not create default cluster. Please create it manually with


  pg_createcluster 9.4 main --start


or a similar command (see 'man pg_createcluster').
update-alternatives: using /usr/share/postgresql/9.4/man/man1/postmaster.1.gz to provide /usr/share/man/man1/postmaster.1.gz (postmaster.1.gz) in auto mode
 * No PostgreSQL clusters exist; see "man pg_createcluster"
Setting up postgresql (9.4+166.pgdg14.04+1) ...
Setting up postgresql-contrib-9.4 (9.4.1-1.pgdg14.04+1) ...
Setting up postgresql-contrib (9.4+166.pgdg14.04+1) ...



```

Which I'm counting as progress!

```
which psql 
```returns```
 /usr/bin/psql 
```so I think it's installed just has issues.

---

### Post by l-l-pajuelo on 2015-05-10
No joy
```
$ ls -l /dev/nullcrw-rw-r-- 1 root leslie 1, 3 May 10 07:41 /dev/null
```
I have permissions on the folder but it's still blocking


```
leslie@leslie:~$ sudo pg_createcluster 9.4 main --start
Creating new cluster 9.4/main ...
  config /etc/postgresql/9.4/main
  data   /var/lib/postgresql/9.4/main
  locale en_US.UTF-8
Flags of /var/lib/postgresql/9.4/main set as -------------e-C
sh: 1: cannot create /dev/null: Permission denied
[...]
sh: 1: cannot create /dev/null: Permission denied
child process exited with exit code 2
initdb: removing contents of data directory "/var/lib/postgresql/9.4/main"
Error: initdb failed

```

[This bug report fixed that problem]("https://answers.launchpad.net/ubuntu/+question/16830")

```
[COLOR=#333333][FONT=Ubuntu]sudo nano /etc/rc.local[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]and put before the exit 0 instruction[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]chmod 0666 /dev/null <---- insert this[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]exit 0 <--- don't touch this row[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Save and reboot[/FONT][/COLOR]

```

---

### Post by l-l-pajuelo on 2015-05-10
When I tried to run psql I got 

```
$ psqlpsql: FATAL:  role "leslie" does not exist
```

The wiki very unhelpfully suggested I create a new user > 
FATAL: role "myusername" does not exist

By default PostgreSQL connects to the PostgreSQL user with the same name as the current unix user. You have not created a PostgreSQL user by that name in your database.
Create a suitable user, or specify a different username to connect with. In the command line tools the -U flag does this. Which would be great if I could use "createuser -U" but alas I cannot.

However! 
```

createuser --interactive
createdb
psql

```

Worked!
Thank you Dino99 for getting me on the right track.

---

### Post by douglasroyer on 2015-07-04
For me, it turns out that I had a non-issued version of perl in my path. It was running /usr/local/bin/perl, when I disabled that one (renamed it), it then used /usr/bin/perl and everything worked fine.

---

