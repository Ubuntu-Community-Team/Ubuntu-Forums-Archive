---
title: "Error installing JAVA"
date: 2007-03-17
forum: General Help
---

### Post by mzvertigo on 2007-03-17
hi everyone,

Im very new to linux and ubuntu and tried installing JAVA on my laptop using the 
following codes:

```

sudo aptitude update
sudo aptitude install sun-java5-plugin

```

and i get the following message.  Any help would be appreciated.  Thanks!


ecg366@ecg366-laptop:~$ sudo aptitude install sun-java5-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  java-common libltdl3 odbcinst1debian1 unixodbc 
The following packages have been kept back:
  sun-java5-bin 
The following NEW packages will be installed:
  sun-java5-plugin 
0 packages upgraded, 1 newly installed, 4 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 1585kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Error!
E: I wasn't able to locate a file for the sun-java5-bin package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
ecg366@ecg366-laptop:~$

---

### Post by zvacet on 2007-03-17
[https://help.ubuntu.com/community/Java?highlight=%28java%29]("https://help.ubuntu.com/community/Java?highlight=%28java%29")

---

### Post by phossal on 2007-03-17
You could always just pull it from Sun, the way I do. Using the packages is a waste of time.

---

