---
title: "Sort files with underscores first in Linux (system wide and not just in terminal)"
date: 2018-03-29
forum: General Help
---

### Post by dalvand on 2018-03-29
I'd like to change the sorting method in Linux (Lubuntu) system wide to get the following sorting result:

    _1.txt
    _a.txt
    _c.txt
    2.txt
    201.txt
    21.txt
    210.txt
    a.txt    
    b.txt
    d.txt

Here is the default sorting that I get using `ls` in terminal and PCManFM:

    _1.txt
    201.txt
    210.txt
    21.txt
    2.txt
    _a.txt
    a.txt
    b.txt
    _c.txt
    d.txt

and here is the sorting result when I set `LC_COLLATE` to `C` by using the command `LC_COLLATE=C ls`:

    2.txt
    201.txt
    21.txt
    210.txt
    _1.txt
    _a.txt
    _c.txt
    a.txt
    b.txt
    d.txt


The `locale` command output on my machine is:

LANG=en_US.UTF-8                                                                               
    LANGUAGE=en_US                                                                                 
    LC_CTYPE="en_US.UTF-8"                                                                         
    LC_NUMERIC="en_US.UTF-8"                                                                       
    LC_TIME="en_US.UTF-8"                                                                          
    LC_COLLATE=en_US.UTF-8                                                                         
    LC_MONETARY="en_US.UTF-8"                                                                      
    LC_MESSAGES="en_US.UTF-8"                                                                      
    LC_PAPER="en_US.UTF-8"                                                                         
    LC_NAME="en_US.UTF-8"                                                                          
    LC_ADDRESS="en_US.UTF-8"                                                                       
    LC_TELEPHONE="en_US.UTF-8"                                                                     
    LC_MEASUREMENT="en_US.UTF-8"                                                                   
    LC_IDENTIFICATION="en_US.UTF-8"                                                                
    LC_ALL=


This question is not a duplicate of the below one as it is mainly for `ls` and I need to have the desired sorting to work system wide and in other applications like PCManFm, double commander, crusader, etc.
[https://unix.stackexchange.com/questions/39827/how-do-i-make-ls-sort-underscore-characters-first](https://unix.stackexchange.com/questions/39827/how-do-i-make-ls-sort-underscore-characters-first)

---

### Post by dalvand on 2018-03-31
Any comment on this?

---

### Post by HermanAB on 2018-04-01
Hmm...
$ man sort

---

