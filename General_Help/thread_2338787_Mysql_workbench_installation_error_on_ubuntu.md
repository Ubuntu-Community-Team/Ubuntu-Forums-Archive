---
title: "Mysql workbench installation error on ubuntu"
date: 2016-10-01
forum: General Help
---

### Post by Liamdale on 2016-10-01
I found today that my version of mysql Workshop (v6) has been un-installed. I did not un-install, I can only assume that a ubuntu update or a new installation on my part is the culprit. I have recently upgraded my version of MySQL to 5.6.33. I tried to reinstall mysql workshop using the installation center but received the error message: Package dependencies cannot be resolved The following packages have unmet dependencies: mysql-workbench: Depends: libgcc1 (>= 1:4.1.1) but 1:4.9.3-0ubuntu4 is to be installed Depends: libgtkmm-2.4-1c2a (>= 1:2.24.0) but 1:2.24.4-1ubuntu1 is to be installed Depends: libpcrecpp0 (>= 7.7) but 1:8.31-2ubuntu2.3 is to be installed Depends: python:any (>= 2.7.1-0ubuntu2) but it is a virtual package Depends: mysql-workbench-data (= 6.0.8+dfsg-2) but 6.0.8+dfsg-2 is to be installed Installation using the terminal gives me the following error message: The following packages have unmet dependencies: mysql-workbench : Depends: mysql-client E: Unable to correct problems, you have held broken packages. Workbench can not find my version of mySQL 5.6.33 ?? Research on the web has not been fruitful. Can anyone help ?

---

