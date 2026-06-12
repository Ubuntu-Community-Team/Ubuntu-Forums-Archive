---
title: "Sudo apt update problems"
date: 2022-04-07
forum: General Help
---

### Post by yoshiki2 on 2022-04-07
Can someone tell me how to fix the duplicates I have ?


```
(base) alfredo@alfredo-hpelitebook725g4:~$ sudo apt update
[sudo] password for alfredo: 
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish InRelease
Hit:2 [https://dl.google.com/linux/chrome/deb](https://dl.google.com/linux/chrome/deb) stable InRelease                                                                                                                               
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish-updates InRelease [115 kB]                                                                                                                 
Hit:4 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) impish InRelease                                                                                                                                  
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) impish-security InRelease [110 kB]                                                                                                                  
Hit:6 [http://repo.mysql.com/apt/ubuntu](http://repo.mysql.com/apt/ubuntu) impish InRelease                                                                                                                 
Hit:7 [https://packages.microsoft.com/repos/edge](https://packages.microsoft.com/repos/edge) stable InRelease                                                                                   
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish-backports InRelease [101 kB]                                                 
Hit:9 [https://cloud.r-project.org/bin/linux/ubuntu](https://cloud.r-project.org/bin/linux/ubuntu) impish-cran40/ InRelease                                  
Fetched 326 kB in 2s (211 kB/s)                                                                              
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up to date.
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge-dev.list:1
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge-dev.list:1
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge-dev.list:1
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge-dev.list:1
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge-dev.list:1
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge-dev.list:1
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge-dev.list:1
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge-dev.list:1
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge-dev.list:1
W: Target DEP-11-icons-large (main/dep11/icons-128x128.tar) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge-dev.list:1
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge-dev.list:1
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge-dev.list:1
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge.list:3                                                                                                                                                               
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge.list:3                                                                                                                                                                 
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge.list:3                                                                                                                                                          
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge.list:3
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge.list:3
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge.list:3
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge.list:3
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge.list:3
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge.list:3
W: Target DEP-11-icons-large (main/dep11/icons-128x128.tar) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge.list:3
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge.list:3
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge.list:3
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge-dev.list:1
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge-dev.list:1
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge-dev.list:1
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge-dev.list:1
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge-dev.list:1
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge-dev.list:1
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge-dev.list:1
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge-dev.list:1
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge-dev.list:1
W: Target DEP-11-icons-large (main/dep11/icons-128x128.tar) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge-dev.list:1
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge-dev.list:1
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge-dev.list:1
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge.list:3
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge.list:3
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge.list:3
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge.list:3
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge.list:3
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge.list:3
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge.list:3
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge.list:3
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge.list:3
W: Target DEP-11-icons-large (main/dep11/icons-128x128.tar) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge.list:3
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge.list:3
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list:1 and /etc/apt/sources.list.d/microsoft-edge.list:3
```

---

### Post by deadflowr on 2022-04-07
Remove either the
```
/etc/apt/sources.list.d/archive_uri-https_packages_microsoft_com_repos_edge-impish.list
``` 
file
or the 
```
/etc/apt/sources.list.d/microsoft-edge-dev.list
```
file

---

### Post by ActionParsnip on 2022-04-08
You can't have the same source of files in multiple files. It confuses apt

---

### Post by yoshiki2 on 2022-04-08
Thanks. I had to remove both Microsoft files for it to work!

---

