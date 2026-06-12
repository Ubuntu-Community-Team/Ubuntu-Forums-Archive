---
title: "[SOLVED] Ubuntu MATE 18.04 x64 - I can't install PAGE.."
date: 2020-03-26
forum: General Help
---

### Post by aquerci on 2020-03-26
Hi guys,

unfortunately I have some issues when I try to install PAGE (a Python GUI generator) in my Linux distribution (Ubuntu MATE 18.04 x64). I downloaded it from the official site ([http://page.sourceforge.net/](http://page.sourceforge.net/)) and I extracted the archive ".tgz". 

the result is a folder with many files inside and among of them there is the "configure" file too. to install the software I wanted to use the following commans:
```

./configure
make
make install

```

the first command should generate the "make" file, but instead it generates this output:
> 
andrea@ubuntu:~/Downloads/page$ ./configure 
Configuring page


Using /usr/bin/wish8.6

#-------- Generated page --------------#
#!/bin/sh


PATH_TO_WISH=/usr/bin/wish8.6
PAGE_HOME=/home/andrea/Downloads/page


export PATH_TO_WISH
export PAGE_HOME


exec ${PATH_TO_WISH} ${PAGE_HOME}/page.tcl "$*"
#-------- End of page -----------------#
andrea@ubuntu:~/Downloads/page$ 




I don't understand. what should I do to install PAGE on my Linux distribution?

---

### Post by aquerci on 2020-03-26
I solved! the command "./configure" generates a script named "page.tcl" and it can be used to open the software.

---

