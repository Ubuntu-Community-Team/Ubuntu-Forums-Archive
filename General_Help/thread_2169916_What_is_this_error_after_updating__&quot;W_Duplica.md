---
title: "What is this error after updating:  &quot;W: Duplicate sources.list&quot;"
date: 2013-08-24
forum: General Help
---

### Post by babakflame on 2013-08-24
Hi

 After I run Sudo apt-get update in terminal I got this at the end :


```
Reading package lists... Done
W: Duplicate sources.list entry http://ir.archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages (/var/lib/apt/lists/ir.archive.ubuntu.com_ubuntu_dists_quantal_main_binary-amd64_Packages)

```

what is this error and how can I solve it?

Regards
  Bobi

---

### Post by deadflowr on 2013-08-24
Post the output of
```
cat /etc/apt/sources.list
```

And we'll see what entries are dupes.

---

### Post by babakflame on 2013-08-24
Hi

This is the output of ```
cat /etc/apt/sources.list
```

```
babak@babak-System:~$ cat /etc/apt/sources.list
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://ir.archive.ubuntu.com/ubuntu/ quantal main restricted universe multiverse 
deb-src http://ir.archive.ubuntu.com/ubuntu/ quantal main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://ir.archive.ubuntu.com/ubuntu/ quantal-security main restricted universe multiverse 
deb http://ir.archive.ubuntu.com/ubuntu/ quantal-updates main restricted universe multiverse 
deb http://ir.archive.ubuntu.com/ubuntu/ quantal-proposed main restricted universe multiverse 
deb http://ir.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse 
deb-src http://ir.archive.ubuntu.com/ubuntu/ quantal-security main restricted universe multiverse 
deb-src http://ir.archive.ubuntu.com/ubuntu/ quantal-updates main restricted universe multiverse 
deb-src http://ir.archive.ubuntu.com/ubuntu/ quantal-proposed main restricted universe multiverse 
deb-src http://ir.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse 

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu quantal partner
deb-src http://archive.canonical.com/ubuntu quantal partner

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://ir.archive.ubuntu.com/ubuntu/ quantal main restricted universe multiverse 
deb-src http://ir.archive.ubuntu.com/ubuntu/ quantal main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://ir.archive.ubuntu.com/ubuntu/ quantal-security main restricted universe multiverse 
deb http://ir.archive.ubuntu.com/ubuntu/ quantal-updates main restricted universe multiverse 
deb http://ir.archive.ubuntu.com/ubuntu/ quantal-proposed main restricted universe multiverse 
deb http://ir.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse 
deb-src http://ir.archive.ubuntu.com/ubuntu/ quantal-security main restricted universe multiverse 
deb-src http://ir.archive.ubuntu.com/ubuntu/ quantal-updates main restricted universe multiverse 
deb-src http://ir.archive.ubuntu.com/ubuntu/ quantal-proposed main restricted universe multiverse 
deb-src http://ir.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse 

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu quantal partner
deb-src http://archive.canonical.com/ubuntu quantal partner


```

   Regards
     Bobi

---

### Post by bapoumba on 2013-08-24
All your entries are in double, Please remove the second instance of your **OFFICIAL UBUNTU REPOS**.

---

### Post by babakflame on 2013-08-25
Hi bapoumba


 Thanks , I will do that.

   Bobi

---

### Post by bapoumba on 2013-08-25
Welcome, please report back to state if that was the problem or if there is still something going on :)

---

### Post by babakflame on 2013-08-31
Hi bapoumba

  It seems that everything is OK. and I have not been confronted with this error.
  
 Regards
     Bobi

---

### Post by bapoumba on 2013-08-31
Good, glad to see you got it to work :)

---

