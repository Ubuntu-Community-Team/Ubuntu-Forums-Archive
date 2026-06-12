---
title: "[SOLVED] ls command colour schema"
date: 2007-12-18
forum: General Help
---

### Post by grahambo2005 on 2007-12-18
Hey all

just a very simple question

when i run the ls command in the terminal I see a list of files and folders in that terminal

but they are all different colours!

what do the colours mean? I know royal blue is a directory, but thats it.

I'm asking this because I cannot start apache. Its saying it cannot find etc/apache2/mods-enabled/autoindex.conf

so I checked for myself and the file is there but it is in red.

any ideas?

Graham

---

### Post by spai on 2007-12-18
**Color 	File type**
blue---------- 	          directories
red---------- 	          compressed archives
white---------	         text files
pink--------	  	   images
cyan---------	         links
yellow -------	        devices
green ---------	        executables
flashing red---------- broken links

---

### Post by grahambo2005 on 2007-12-18
thanks dude

any idea whats wrong with apache then?

heres the error

* Starting web server apache2
apache2: Syntax error on line 184 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/mods-enabled/autoindex.conf: No such file or directory
   ...fail!

Weird

can apache not acces this because it is compressed? how might it have gotten compressed in the first place? I installed mysql server last night maybe thats what caused the problem? this was working fine until last this monring

Graham

---

### Post by spai on 2007-12-18
Really?? mine are links not compressed...
Since it says syntax error, the file might have messed up.I do not know how to solve it. But you can check the line it.
Mine reads ```
Include /etc/apache2/mods-enabled/*.conf
```
Which means it is trying to include all config files at start-up and the autoindex.conf link is ** broken**. SO my guess is that it is FLASHING RED not just RED.
If that is true you will have to replace the broken link. I am not sure how to do it, probably reinstall...

---

### Post by grahambo2005 on 2007-12-18
ran sudo apt-get upgrade apache2

this fixed the problem

---

