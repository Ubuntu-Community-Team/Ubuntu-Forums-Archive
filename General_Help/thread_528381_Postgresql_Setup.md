---
title: "Postgresql Setup"
date: 2007-08-17
forum: General Help
---

### Post by zedmaster on 2007-08-17
Here is my situation.  I'm trying to set up a GIS workstation on this here PC.  I've been trying for a couple months now.  Basically, I am working from the Ubuntu Wiki entry on UbuntuGIS.  

My specs:

Ubuntu Fiesty 7.04, 64 bit version
1 Gb dram
2.2 gHz Athlon 64
ATI X200 built in video

I've tried to install the postgresql 8.1 package from synaptic.  The problem is that the instructions for setting up Postgresql are for building it from source.  All of the file locations are different.  I have also tried uninstalling that package, and building from source as per the postgresql instructions.  This gets me a little bit further.  Once I've got it installed, it then says to set the paths in my environment variables so the system can find the binaries (apparently).  The postgresql user is unable to execute "initdb," however for some reason  my normal user account is able to execute it.    

Can anybody give me some basic instructions on how to install postgresql 8.1 on an Ubuntu Fiesty machine running 64 bit?  I should say installation and setup instructions.  As far as I know, there is no such info available for Ubuntu, let alone 64 bit.  I know that some of you out there can solve a problem like this with a snap of your fingers.  If you do, I will mail you a batch of the best oatmeal cookies you've ever had, OR a check for a 12 pack of beer of your choice.  Seriously.  

Thanks!

---

### Post by bDerrly on 2007-10-28
This is really quick-n-dirty but should work for you. I just set this up tonight on 64-bit Gutsy with PostgreSQL 8.2. This will allow your system user name be a super-user and log in to any database without password. If you need more security than that it'll require more work and probably hacking around with /etc/postgresql/8.2/main/pg_hba.conf.

```
$ sudo aptitutude install postgresql-8.2
$ sudo -s
# su -c postgres
# psql template1
template1=# ALTER USER postgres WITH PASSWORD 'password';
template1=# \q
/* create a user for yourself with super user privileges */
# createuser -s -P <user>
# logout
$ createdb <dbname>
$ psql <dbname>
```

---

