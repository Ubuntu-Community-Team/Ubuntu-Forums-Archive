---
title: "How to made an ODBC connection?"
date: 2007-07-16
forum: General Help
---

### Post by jodoj80 on 2007-07-16
Hi:

I've been trying to setup an ODBC connection from my new Ubuntu web server. I've already install: Apache, MySQL and PHP. 

I read in other post that I can use ```
sudo apt-get install libmyodbc
```But, when I press ENTER in the terminal it says ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libmyodbc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libmyodbc has no installation candidate
```

I'm trying to upload a local website in my work and I need to establish a ODBC connection to the data base.

Regards,

---

### Post by dcstar on 2007-07-17
> **jodoj80 said:**
> Hi:

I've been trying to setup an ODBC connection from my new Ubuntu web server. I've already install: Apache, MySQL and PHP. 

I read in other post that I can use ```
sudo apt-get install libmyodbc
```But, when I press ENTER in the terminal it says ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libmyodbc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libmyodbc has no installation candidate
```

I'm trying to upload a local website in my work and I need to establish a ODBC connection to the data base.

Regards,

My Synaptic says that this package has (at least) 3 dependencies, why don't you use that tool to install the whole lot?

---

### Post by jodoj80 on 2007-07-17
Thanks David for your help. But, I'm noob with Ubuntu. How can I install the package from Synaptic Package Manager? Because, I couldn't find the libmyodbc in the list.

Regards,

---

### Post by dgermann on 2007-08-15
jodoj80--

Did you ever find an answer?

If not, synaptic is a menu item. On 6.06 it is System> Administration> Synaptic.

And did that package work for you? Not for me so far, but I found a thread here that might help with my problem:
[http://www.flatmtn.com/computer/Linux-mySQL.html#mySQLiODBC-1]("http://www.flatmtn.com/computer/Linux-mySQL.html#mySQLiODBC-1")

:- Doug.

---

