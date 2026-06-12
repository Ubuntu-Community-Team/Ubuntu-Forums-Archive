---
title: "PHP4 not recognising MySQL functions"
date: 2004-12-09
forum: General Help
---

### Post by Crisp on 2004-12-09
Hi
    
 I have installed Apache 1.3, and PHP4 is working fine with it. I also know that MySQL is up and running fine, and I have no problems using phpmyadmin. However, when it comes to using mysql_connect() I get the following error:
    
     **Fatal error**:  Call to undefined function:  mysql_connect() in **/home/crisp/www/myapp/dbconn.php** on line [b]2
    
    [/b]I have installed php4-mysql via apt-get, which is described as a package that "provides a module for MySQL database connections directly from PHP scripts", so I don't see what the problem is. 
    
    Any ideas?  Thanks,
    
    -Crisp

---

### Post by kagou on 2004-12-17
Same problem here.
Phpmyadmin work like a charm.
But when i want to install punbb (board) or plume (CMS) they say me that there are no PHP module  for mysql (php4-mysql is installed of course)

---

### Post by Crisp on 2004-12-19
Kagou, even though I compiled PHP with mysql, it didn't want to know.  I went back to Apache2 and it works fine.  I'm not too happy about developing on an apache2 server, but it does the job for now.
 
 -Crisp

---

### Post by deuce868 on 2005-03-07
Did you guys ever get this squared away? I am having the same problems on apache2 on hoary. 

See thread here:
[http://www.ubuntuforums.org/showthread.php?t=18514](http://www.ubuntuforums.org/showthread.php?t=18514)

Thanks

---

