---
title: "Display the amount of memory being USED"
date: 2016-05-25
forum: General Help
---

### Post by alex_charters2 on 2016-05-25
Hi All 
I would like to be able to display the amount of memory used in gigabytes and as a percentage in the terminal if this is possible if not gigabytes then megabytes would do

thanks for the help in advanced
Alex

---

### Post by sudodus on 2016-05-25
The simplest tool is ***free***.

```
free
free -m
free -g
```

See ```
man free
``` for details.

You can also run ***top***, or install and run ***htop***,

```
sudo apt-get install htop
```

---

### Post by alex_charters2 on 2016-05-25
thanks for the reply but do you know how to get it to display just the memory that is in use.

---

### Post by sudodus on 2016-05-25
The way free is displaying depends on the version. In Ubuntu 16.04 LTS there is ***free version 3.3.10*** and it displays like this:

```
$ free -m
              total        used        free      shared  buff/cache   available
Mem:           4041         524        2376          19        1139        3452
Swap:         16399           8       16391
```

If you use tr, grep and cut, you can display only used memory:

Condense the separating spaces to a TAB, select the line containing Mem:, and print the third field of that line,

```
free -m | tr -s ' ' '\t' | grep Mem: | cut -f3
```

---

