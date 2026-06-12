---
title: "GForge installation"
date: 2005-05-09
forum: General Help
---

### Post by Neloc on 2005-05-09
Hello I'm quite new to Linux and have been trying to install gforge using sudo apt-get install gforge. The installation failes around the setup of gforge-web-apache with the error that it cannot stat /etc/php4/apache.ini as shown below.

I have installed php4 using the get command previously but it is located in /etc/php4/apache2/php.ini. 

Does anyone know how I would go about fixing this problem, or where I might need to go for assistance?

Marcel 

[I]
Setting up gforge-web-apache (3.1-24) ...
cp: cannot stat `/etc/php4/apache/php.ini': No such file or directory
dpkg: error processing gforge-web-apache (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gforge:
 gforge depends on gforge-web-apache | gforge-web; however:
  Package gforge-web-apache is not configured yet.
  Package gforge-web is not installed.
  Package gforge-web-apache which provides gforge-web is not configured yet.
dpkg: error processing gforge (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gforge-web-apache
 gforge
E: Sub-process /usr/bin/dpkg returned an error code (1)[/i]


Thanks

---

### Post by tread on 2005-05-09
> gforge depends on gforge-web-apache | gforge-web; however: 
Package gforge-web-apache is not configured yet. 
Package gforge-web is not installed. 
Package gforge-web-apache which provides gforge-web is not configured yet. 

I'm guessing you are trying to install a single file using dpkg -i.
If you look at the output, it says that some packages which are needed (dependency) are not installed. Try getting those packages too, and installing them first.

---

### Post by Neloc on 2005-05-09
Hey thanks for the response.

gforge is dependent on gforge-web-apache, however gforge-web-apache is failing because it is canont stat /etc/php4/apache/php.ini

php.ini is located in /etc/php4/apache2/php.ini, I tried manually changing the directory name and this allowed it to move forward one or two steps after which the installation just crashed and halted. 

PHP4 was actually installed by the as a dependency during an apt-get of gforge which is why I am a bit unsure of how to handle the problem.

---

### Post by tread on 2005-05-09
Could you put up some more output of the crash? That may help us .. and if all else fails there is always compiling from source :)

I may be a bit slow in replying .. I have to leave for my exams soon.  :mad: 
Hopefully someone else can help you, else I shall try when I next come online.

---

### Post by Neloc on 2005-05-09
Cheers,

That was the full output after the 3rd attempted reinstall of gforge. I will remove all the packages and dependencies and reinstall from scratch so that I can give you the full output.

---

