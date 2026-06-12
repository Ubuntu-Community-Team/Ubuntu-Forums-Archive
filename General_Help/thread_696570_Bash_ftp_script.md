---
title: "Bash ftp script"
date: 2008-02-14
forum: General Help
---

### Post by aaronp on 2008-02-14
Hi all,
I know this is not an Ubuntu specific topic but feel someone might know how to fix easily.

I am writing a bash script to use ftp to download all files in the directory structure of my website on a daily basis as a backup.

Everything works perfectly except none of the files copy. The directories are created, the ftp connection ovvurs and the directory is changed on the remote system but nothing downloads.
If I change it it download a specific filename using get instead of mget it does actually download.


Here is the script file (I have changed some things for security and enclose them inside <>)

#!/bin/bash
NOW=$(date +"%Y%m%d")
mkdir /media/hdb8/Aaron/sleeplever/$NOW
cd /media/hdb8/Aaron/sleeplever/$NOW
mkdir images
cd images
mkdir Dave
ftp -vni <server> <<EOD
quote USER <user>
quote PASS <pass>
passive
lcd /media/hdb8/Aaron/sleeplever/$NOW
cd sleeplever.com
mget *.*
lcd images
cd images
mget *.*
lcd Dave
cd Dave
mget *.*
quit
EOD
exit 0


thanks in advance
Aaron

---

### Post by hahahan on 2008-02-14
You could try to use "wget" , it has powerfull options like -r and -l n. See man wget.

Regards.

---

