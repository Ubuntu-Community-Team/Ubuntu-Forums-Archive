---
title: "mdbtools help"
date: 2007-05-21
forum: General Help
---

### Post by lenny8088 on 2007-05-21
Trying to apt-get the mdbtools and mdbtools-odbc and at first it just wouldn't find them. After trying a fair amount of different things I now get...
> wht:/etc$ sudo apt-get install mdbtools
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libmdbtools: Depends: libglib2.0-0 (>= 2.12.0) but it is not going to be installed
  mdbtools: Depends: libglib2.0-0 (>= 2.12.9) but it is not going to be installed
  mdbtools-dev: Depends: libmdbtools (= 0.5.99.0.6pre1.0.20050409-1) but 0.5.99.0.6pre1.0.20051109-4 is to be installed
                Depends: libglib2.0-dev but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


And it tells me the same thing when I try to get libglib2.0-0. 

Any help is appreciated - hasn't been a successful day so far.

---

### Post by lenny8088 on 2007-05-21
I got it. Key part was "no packages". Didn't use the eyes that horrible Cthulhu saw fit to give me.

---

