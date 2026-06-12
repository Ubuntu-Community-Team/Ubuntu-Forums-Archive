---
title: "[Solved] Lubuntu Flavitu 14.04 error on upgrade ."
date: 2016-11-12
forum: General Help
---

### Post by Portaro on 2016-11-12
I have an error with my upgrade command &#8594;

> sudo apt-get upgradeA ler as listas de pacotes... Erro !
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntugames.org_dists_ubuntugames_main_i18n_Translation-en
E: As listas de pacotes ou o ficheiro de status não pôde ser analisado ou aberto.




I try  -  $ sudo rm -vf /var/lib/apt/lists/*
But then when I do a :
$ sudo apt-get update
and
$ sudo apt-get upgrade 

the problem returns and I think that I cant receive upgrades of software because this .

Any idea how to solve this?

Thanks.:popcorn:

---

### Post by Portaro on 2016-11-14
Little solution is edit /etc/apt/sources.list on the line of repo &#8594;

##ubuntugames
# deb [http://archive.ubuntugames.org](http://archive.ubuntugames.org) ubuntugames main
# deb-src [http://archive.ubuntugames.org](http://archive.ubuntugames.org) ubuntugames main

---

