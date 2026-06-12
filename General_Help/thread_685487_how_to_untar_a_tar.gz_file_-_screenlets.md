---
title: "how to untar a tar.gz file - screenlets"
date: 2008-02-02
forum: General Help
---

### Post by kystorms on 2008-02-02
hello

I have downloaded screenlets which is a tar.bz2 file. 
Using the commands given on this page - [http://www.freebsddiary.org/untar.php](http://www.freebsddiary.org/untar.php)

I used the following code:
tar yxf something.tar.bz2

but got this error:
lisac@lisac-desktop:~$ tar yxf screenlets-0.0.0.tar.bz2
tar: invalid option -- y
Try `tar --help' or `tar --usage' for more information.
lisac@lisac-desktop:~$ 
lisac@lisac-desktop:~$ 

Would someone tell me if I am supposed to either:

take the numbers off the file name  OR
am i supposed to do something before I try to untar the file?

thank you

---

### Post by thirunavukkarasu on 2008-02-02
Hi 

just type 

**$tar -jxvf screenlets-0.0.0.tar.bz2**

tar is the command  and -jxvf are options to the command

for any command usage first read the man page. to get the man page in your terminal

type "man command"; in your case type "man tar"

regards
thiru.S

---

