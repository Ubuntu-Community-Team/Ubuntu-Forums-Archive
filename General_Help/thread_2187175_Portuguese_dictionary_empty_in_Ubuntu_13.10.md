---
title: "Portuguese dictionary empty in Ubuntu 13.10"
date: 2013-11-11
forum: General Help
---

### Post by lads on 2013-11-11
Hello everyone,

I just installed the Portuguese dictionary on Ubuntu 13.10 but no application is able to use it. Checking in the command line it seems this dictionary is empty:

```
$ sudo aptitude search aspell-pt
p   aspell-pt                                                 - Portuguese dictionaries for GNU Aspell (old package)               
p   aspell-pt-br                                              - Brazilian Portuguese dictionary for GNU Aspell                     
i   aspell-pt-pt                                              - European Portuguese dictionary for GNU Aspell  
$ aspell dicts | grep pt
pt_PT
$ aspell -l pt_PT dump master
$ 
```

Could I be missing some package or is this a bug that should be reported? Thanks.

---

### Post by lads on 2013-11-18
Any hints on this issue are welcome. Thank you.

---

### Post by lads on 2013-11-25
Anyone?

---

### Post by lads on 2013-12-03
This problem still persists.

---

### Post by lads on 2013-12-14
I finally managed to solved this problem. This is [a bug that first appeared in Lucid]("https://bugs.launchpad.net/ubuntu/+source/myspell.pt/+bug/568088") and persisted with Oneiric. For some reason it has re-emerged in Saucy. The difficulty was then to find a source for the dictionary, which eventually [I did]("http://natura.di.uminho.pt/download/sources/Dictionaries/aspell6"). The fix is then:

```

cd /tmp
wget http://natura.di.uminho.pt/download/sources/Dictionaries/aspell6/aspell6.pt-20131211.tar.bz2
tar xjf aspell6.pt-20131211.tar.bz2
cd aspell6-pt_PT-20131211-0
./configure
make
sudo make install
```

---

