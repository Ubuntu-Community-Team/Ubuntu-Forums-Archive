---
title: "Postgres configuration error on install"
date: 2018-06-26
forum: General Help
---

### Post by clayton3 on 2018-06-26
I'm trying to install the postgres client on a Continous Integration server. I've followed the steps in this thread: [https://ubuntuforums.org/showthread.php?t=2277582](https://ubuntuforums.org/showthread.php?t=2277582). When I `ssh` into the server, I have the client available, but during the install I'm thrown this error:

```
dpkg: error processing package postgresql-client-9.6 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of postgresql-client:
 postgresql-client depends on postgresql-client-9.6; however:
  Package postgresql-client-9.6 is not configured yet.

dpkg: error processing package postgresql-client (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 postgresql-client-9.6
 postgresql-client
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

That error kills the CI process, which means I can't finish the build. My two options are 

1. Install/configure in a way that doesn't throw an error
2. Silence the error and keep building.

I've tried the second, but it still throws the error.
```
sudo apt-get -qq install postgresql-client > /dev/null
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I did try the cleanup suggestion from the post linked above:

```
[FONT=arial]sudo apt-get purge postgr*
sudo apt-get autoremove
sudo apt-get install synaptic
sudo apt-get update[/FONT]
```[FONT=arial]

And...

```
which psql
/usr/bin/psql
```

And.. 
```
more /etc/apt/sources.list
deb http://deb.debian.org/debian stretch main
deb http://deb.debian.org/debian stretch-updates main
deb http://security.debian.org/debian-security stretch/updates main
```[/FONT]

---

### Post by SeijiSensei on 2018-06-26
What if you run "sudo dpkg --configure -a"?

---

### Post by clayton3 on 2018-06-27
> **SeijiSensei said:**
> What if you run "sudo dpkg --configure -a"?

```
Setting up postgresql-client-9.6 (9.6.7-0+deb9u1) ...
update-alternatives: using /usr/share/postgresql/9.6/man/man1/psql.1.gz to provide /usr/share/man/man1/psql.1.gz (psql.1.gz) in auto mode
update-alternatives: error: error creating symbolic link '/usr/share/man/man7/ABORT.7.gz.dpkg-tmp': No such file or directory
dpkg: error processing package postgresql-client-9.6 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of postgresql-client:
 postgresql-client depends on postgresql-client-9.6; however:
  Package postgresql-client-9.6 is not configured yet.

dpkg: error processing package postgresql-client (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 postgresql-client-9.6
 postgresql-client
```

It looks like it might be related to this issue in Debian. But I'm not sure how to determine if the update has, uh, percolated to Ubuntu.

[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=866729](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=866729)

The significant part of the error is `update-alternatives: error: error creating symbolic link '/usr/share/man/man7/ABORT.7.gz.dpkg-tmp': No such file or directory`. Can I simple create the missing file?

---

