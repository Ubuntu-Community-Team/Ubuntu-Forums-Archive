---
title: "Error with C++ sanity check and ./configure"
date: 2005-05-05
forum: General Help
---

### Post by nightshrill on 2005-05-05
Please forgive me if this thread is in the wrong category however here is my current issue. I'm trying to compile kmymoney from source, and when running ./configure I snag this nasty little error

checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.

I've gone through synaptic and installed just about everything that had libcpp and cpp (yeah, the newb thing to do) hoping it would work afterwards, but to no avail it has not. So can anyone lend a good ol' newbie to ubuntu a hand? :smile:

---

### Post by Xerampelinae on 2005-05-05
I don't know, but I think checking config.log for information would be a good idea.

---

### Post by nightshrill on 2005-05-06
[QUOTE=Xerampelinae]I don't know, but I think checking config.log for information would be a good idea.[/QUOTE]

The only thing I learned from the config.log is this:

| 		     Syntax error
configure:5442: result: /lib/cpp
configure:5466: /lib/cpp  conftest.cc
cpp: installation problem, cannot exec `cc1plus': No such file or directory
configure:5472: $? = 1
configure: failed program was:
| /* confdefs.h.  */

which has not helped me at all as I can't find anything in synaptic that I don't have that has ccp as a suffix, and that I cannot locate any package named cclplus.

---

### Post by sindorf on 2005-05-28
Hi,

install g++ to resolve this problem. I have the exact problem. I installed "g++" and it resolved the problem.

but still I am having problems with the PATHs :) but it is due to my prog :)

have a good day :)

---

### Post by acascianelli on 2005-08-19
Did you install g++-3.3 or g++-3.4?

---

### Post by mcmuffy on 2005-09-15
Cool. Seems to have fixed the problem for me also  :)
All hail the search button!!!

---

