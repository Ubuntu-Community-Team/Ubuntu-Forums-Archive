---
title: "I cant install wine 4.0.2 stable because..."
date: 2019-08-25
forum: General Help
---

### Post by jackal29 on 2019-08-25
Hi, How it said above, i cant install wine 4.0.2 stable version because this issue, I am using ubuntu in Spanish, here the issue:


```

juancarlos@juancarlos-B450-AORUS-M:~$ sudo apt-add-repository 'deb https://dl.winehq.org/wine-builds/ubuntu/ bionic main'
Obj:1 https://dl.winehq.org/wine-builds/ubuntu cosmic InRelease
Ign:2 http://dl.google.com/linux/chrome/deb stable InRelease                   
Des:3 https://dl.winehq.org/wine-builds/ubuntu bionic InRelease [6.257 B]      
Des:4 http://security.ubuntu.com/ubuntu bionic-security InRelease [88,7 kB]    
Des:5 https://dl.winehq.org/wine-builds/ubuntu bionic/main i386 Packages [515 kB]
Obj:6 http://repo.steampowered.com/steam precise InRelease                     
Obj:7 http://apt.postgresql.org/pub/repos/apt bionic-pgdg InRelease            
Des:8 https://dl.winehq.org/wine-builds/ubuntu bionic/main amd64 Packages [486 kB]
Des:9 http://dl.google.com/linux/chrome/deb stable Release [943 B]             
Des:10 http://dl.google.com/linux/chrome/deb stable Release.gpg [819 B]        
Des:11 http://security.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata [22,7 kB]
Obj:12 http://co.archive.ubuntu.com/ubuntu bionic InRelease                    
Des:13 http://co.archive.ubuntu.com/ubuntu bionic-updates InRelease [88,7 kB]  
Des:14 http://co.archive.ubuntu.com/ubuntu bionic-backports InRelease [74,6 kB]
Des:15 http://security.ubuntu.com/ubuntu bionic-security/main DEP-11 64x64 Icons [31,7 kB]
Des:16 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 DEP-11 Metadata [42,1 kB]
Des:17 http://dl.google.com/linux/chrome/deb stable/main amd64 Packages [1.108 B]
Des:18 http://security.ubuntu.com/ubuntu bionic-security/universe DEP-11 48x48 Icons [16,4 kB]
Des:19 http://security.ubuntu.com/ubuntu bionic-security/universe DEP-11 64x64 Icons [108 kB]
Ign:20 http://wireframesketcher.com/debian  InRelease                          
Des:21 http://security.ubuntu.com/ubuntu bionic-security/multiverse amd64 DEP-11 Metadata [2.464 B]
Obj:22 http://wireframesketcher.com/debian  Release                            
Des:23 http://co.archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata [285 kB]
Des:25 http://co.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 48x48 Icons [70,9 kB]
Des:26 http://co.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 64x64 Icons [140 kB]
Des:27 http://co.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 DEP-11 Metadata [253 kB]
Des:28 http://co.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 48x48 Icons [205 kB]
Des:29 http://co.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 64x64 Icons [453 kB]
Des:30 http://co.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 DEP-11 Metadata [2.468 B]
Des:31 http://co.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 DEP-11 Metadata [7.920 B]
Descargados 2.901 kB en 2s (1.191 kB/s)                                  
Leyendo lista de paquetes... Hecho
W: El objetivo Packages (main/binary-amd64/Packages) está configurado varias veces en /etc/apt/sources.list.d/PostgreSQL.list:1 y /etc/apt/sources.list.d/pgdg.list:1
W: El objetivo Packages (main/binary-i386/Packages) está configurado varias veces en /etc/apt/sources.list.d/PostgreSQL.list:1 y /etc/apt/sources.list.d/pgdg.list:1
W: El objetivo Packages (main/binary-all/Packages) está configurado varias veces en /etc/apt/sources.list.d/PostgreSQL.list:1 y /etc/apt/sources.list.d/pgdg.list:1
W: El objetivo Translations (main/i18n/Translation-es_CO) está configurado varias veces en /etc/apt/sources.list.d/PostgreSQL.list:1 y /etc/apt/sources.list.d/pgdg.list:1
W: El objetivo Translations (main/i18n/Translation-es) está configurado varias veces en /etc/apt/sources.list.d/PostgreSQL.list:1 y /etc/apt/sources.list.d/pgdg.list:1
W: El objetivo Translations (main/i18n/Translation-en) está configurado varias veces en /etc/apt/sources.list.d/PostgreSQL.list:1 y /etc/apt/sources.list.d/pgdg.list:1
W: El objetivo DEP-11 (main/dep11/Components-amd64.yml) está configurado varias veces en /etc/apt/sources.list.d/PostgreSQL.list:1 y /etc/apt/sources.list.d/pgdg.list:1
W: El objetivo DEP-11 (main/dep11/Components-all.yml) está configurado varias veces en /etc/apt/sources.list.d/PostgreSQL.list:1 y /etc/apt/sources.list.d/pgdg.list:1
W: El objetivo DEP-11-icons-small (main/dep11/icons-48x48.tar) está configurado varias veces en /etc/apt/sources.list.d/PostgreSQL.list:1 y /etc/apt/sources.list.d/pgdg.list:1
W: El objetivo DEP-11-icons (main/dep11/icons-64x64.tar) está configurado varias veces en /etc/apt/sources.list.d/PostgreSQL.list:1 y /etc/apt/sources.list.d/pgdg.list:1
W: El objetivo CNF (main/cnf/Commands-amd64) está configurado varias veces en /etc/apt/sources.list.d/PostgreSQL.list:1 y /etc/apt/sources.list.d/pgdg.list:1
W: El objetivo CNF (main/cnf/Commands-all) está configurado varias veces en /etc/apt/sources.list.d/PostgreSQL.list:1 y /etc/apt/sources.list.d/pgdg.list:1
W: El objetivo Packages (main/binary-amd64/Packages) está configurado varias veces en /etc/apt/sources.list.d/PostgreSQL.list:1 y /etc/apt/sources.list.d/pgdg.list:1
W: El objetivo Packages (main/binary-i386/Packages) está configurado varias veces en /etc/apt/sources.list.d/PostgreSQL.list:1 y /etc/apt/sources.list.d/pgdg.list:1
W: El objetivo Packages (main/binary-all/Packages) está configurado varias veces en /etc/apt/sources.list.d/PostgreSQL.list:1 y /etc/apt/sources.list.d/pgdg.list:1
W: El objetivo Translations (main/i18n/Translation-es_CO) está configurado varias veces en /etc/apt/sources.list.d/PostgreSQL.list:1 y /etc/apt/sources.list.d/pgdg.list:1
W: El objetivo Translations (main/i18n/Translation-es) está configurado varias veces en /etc/apt/sources.list.d/PostgreSQL.list:1 y /etc/apt/sources.list.d/pgdg.list:1
W: El objetivo Translations (main/i18n/Translation-en) está configurado varias veces en /etc/apt/sources.list.d/PostgreSQL.list:1 y /etc/apt/sources.list.d/pgdg.list:1
W: El objetivo DEP-11 (main/dep11/Components-amd64.yml) está configurado varias veces en /etc/apt/sources.list.d/PostgreSQL.list:1 y /etc/apt/sources.list.d/pgdg.list:1
W: El objetivo DEP-11 (main/dep11/Components-all.yml) está configurado varias veces en /etc/apt/sources.list.d/PostgreSQL.list:1 y /etc/apt/sources.list.d/pgdg.list:1
W: El objetivo DEP-11-icons-small (main/dep11/icons-48x48.tar) está configurado varias veces en /etc/apt/sources.list.d/PostgreSQL.list:1 y /etc/apt/sources.list.d/pgdg.list:1
W: El objetivo DEP-11-icons (main/dep11/icons-64x64.tar) está configurado varias veces en /etc/apt/sources.list.d/PostgreSQL.list:1 y /etc/apt/sources.list.d/pgdg.list:1
W: El objetivo CNF (main/cnf/Commands-amd64) está configurado varias veces en /etc/apt/sources.list.d/PostgreSQL.list:1 y /etc/apt/sources.list.d/pgdg.list:1
W: El objetivo CNF (main/cnf/Commands-all) está configurado varias veces en /etc/apt/sources.list.d/PostgreSQL.list:1 y /etc/apt/sources.list.d/pgdg.list:1
juancarlos@juancarlos-B450-AORUS-M:~$ 



```

Thank you for your cooperation

---

### Post by cruzer001 on 2019-08-25
From what I make of the translation SQL has more than one entry in sources.list.d.  You need to remove the additional entries and I think your software sources GUI can do that.
```
software-properties-gtk
```

---

### Post by jackal29 on 2019-08-26
thanks thats works a lot.

---

### Post by cruzer001 on 2019-08-26
Your welcome, please mark your thread as solved.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

