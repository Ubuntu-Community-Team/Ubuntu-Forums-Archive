---
title: "Apache2 directoy structure"
date: 2005-05-09
forum: General Help
---

### Post by loucomballa on 2005-05-09
Hi,
I've deleted, by mistake, the /etc/apache2 folder. The problem is that now I cannot recreate it. By uninstalling+installing, via apt-get, apache2 the folder is not created and, as a result, the server cannot start. Of course I could download the sources and compile it but I would like to stick to the Ubuntu packages. How could I recreate all apache2 folders?

Thanks!

X.

---

### Post by daniels on 2005-05-09
sudo dpkg -i --force-confmiss /var/cache/apt/archives/apache2-common_*.deb

---

### Post by loucomballa on 2005-05-10
Thanks, it has worked! :-)

X.

---

### Post by beatyou on 2005-07-08
I had this exact same problem and tried the command given by daniels. But get this error

beatyou@mankind:/etc$ sudo dpkg -i --force-confmiss /var/cache/apt/archives/apache2_2.0.53-5ubuntu5.1_i386.deb
dpkg: error processing /var/cache/apt/archives/apache2-common_*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/apache2-common_*.deb

I also tried command that is the exact .deb for apache from apt-get
sudo dpkg -i --force-confmiss /var/cache/apt/archives/apache2_2.0.53-5ubuntu5.1_i386.deb

Still does not replace /etc/apache2 directory and files within. 

Thanks ahead of time

---

