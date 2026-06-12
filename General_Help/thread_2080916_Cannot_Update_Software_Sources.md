---
title: "Cannot Update Software Sources"
date: 2012-11-05
forum: General Help
---

### Post by gokhanyavuz on 2012-11-05
Hi,
I'm using Ubuntu 10.04 LTS. Cannot update software sources. "Sources.list", "Sources.list.distUpgrade" and "Sources.list.save" files appear updated. However, i don't see in Software Sources interface. When i want to add in Software Sources interface, cannot add.
When i used "sudo apt-get update", console output:
```

Hit http://archive.ubuntu.com lucid Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://archive.ubuntu.com lucid-updates Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://dl.google.com stable Release.gpg
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US
Hit http://archive.ubuntu.com lucid-security Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://archive.ubuntu.com lucid Release    
Hit http://dl.google.com stable Release                              
Hit http://archive.ubuntu.com lucid-updates Release
Hit http://archive.ubuntu.com lucid-security Release                 
Hit http://archive.ubuntu.com lucid/main Packages                    
Hit http://archive.ubuntu.com lucid/restricted Packages
Hit http://archive.ubuntu.com lucid/main Sources
Hit http://archive.ubuntu.com lucid/restricted Sources
Hit http://archive.ubuntu.com lucid/universe Packages
Hit http://archive.ubuntu.com lucid/universe Sources
Hit http://archive.ubuntu.com lucid/multiverse Packages
Hit http://archive.ubuntu.com lucid/multiverse Sources
Hit http://archive.ubuntu.com lucid-updates/main Packages
Hit http://archive.ubuntu.com lucid-updates/restricted Packages
Hit http://archive.ubuntu.com lucid-updates/main Sources
Hit http://archive.ubuntu.com lucid-updates/restricted Sources
Hit http://archive.ubuntu.com lucid-updates/universe Packages
Hit http://dl.google.com stable/main Packages  
Hit http://archive.ubuntu.com lucid-updates/universe Sources
Hit http://archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://archive.ubuntu.com lucid-updates/multiverse Sources
Hit http://archive.ubuntu.com lucid-security/main Packages
Hit http://archive.ubuntu.com lucid-security/restricted Packages
Hit http://archive.ubuntu.com lucid-security/main Sources
Hit http://archive.ubuntu.com lucid-security/restricted Sources
Hit http://archive.ubuntu.com lucid-security/universe Packages
Hit http://archive.ubuntu.com lucid-security/universe Sources
Hit http://archive.ubuntu.com lucid-security/multiverse Packages
Hit http://archive.ubuntu.com lucid-security/multiverse Sources
Reading package lists... Done

```

---

### Post by 2F4U on 2012-11-05
The output doesn't show any error message - or I am just too blind to see it. So to me it seems as if apt-get successfully updated the sofware sources.
To verify that it works, you should also execute

sudo apt-get upgrade

---

### Post by gokhanyavuz on 2012-11-05
The problem still continues. :\ 

"sudo apt-get upgrade" output:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libmysqlclient16 mysql-common
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,986kB of archives.
After this operation, 16.4kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://archive.ubuntu.com/ubuntu/ lucid-updates/main mysql-common 5.1.66-0ubuntu0.10.04.1 [79.3kB]
Get:2 http://archive.ubuntu.com/ubuntu/ lucid-updates/main libmysqlclient16 5.1.66-0ubuntu0.10.04.1 [1,907kB]
Fetched 1,986kB in 6s (312kB/s)                                                
(Reading database ... 132424 files and directories currently installed.)
Preparing to replace mysql-common 5.1.63-0ubuntu0.10.04.1 (using .../mysql-common_5.1.66-0ubuntu0.10.04.1_all.deb) ...
Unpacking replacement mysql-common ...
Preparing to replace libmysqlclient16 5.1.63-0ubuntu0.10.04.1 (using .../libmysqlclient16_5.1.66-0ubuntu0.10.04.1_i386.deb) ...
Unpacking replacement libmysqlclient16 ...
Setting up mysql-common (5.1.66-0ubuntu0.10.04.1) ...
Setting up libmysqlclient16 (5.1.66-0ubuntu0.10.04.1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

---

### Post by drmrgd on 2012-11-05
Can you show us a picture or example of the error you're seeing.  What you've been showing is completely normal behavior!

---

### Post by wirelessmonkey on 2012-11-05
> **gokhanyavuz said:**
> The problem still continues. :\ 

"sudo apt-get upgrade" output:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libmysqlclient16 mysql-common
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,986kB of archives.
After this operation, 16.4kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://archive.ubuntu.com/ubuntu/ lucid-updates/main mysql-common 5.1.66-0ubuntu0.10.04.1 [79.3kB]
Get:2 http://archive.ubuntu.com/ubuntu/ lucid-updates/main libmysqlclient16 5.1.66-0ubuntu0.10.04.1 [1,907kB]
Fetched 1,986kB in 6s (312kB/s)                                                
(Reading database ... 132424 files and directories currently installed.)
Preparing to replace mysql-common 5.1.63-0ubuntu0.10.04.1 (using .../mysql-common_5.1.66-0ubuntu0.10.04.1_all.deb) ...
Unpacking replacement mysql-common ...
Preparing to replace libmysqlclient16 5.1.63-0ubuntu0.10.04.1 (using .../libmysqlclient16_5.1.66-0ubuntu0.10.04.1_i386.deb) ...
Unpacking replacement libmysqlclient16 ...
Setting up mysql-common (5.1.66-0ubuntu0.10.04.1) ...
Setting up libmysqlclient16 (5.1.66-0ubuntu0.10.04.1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

This shows a successful update/install. Where are you seeing errors?

---

