---
title: "ERROR 1045 (28000): Access denied for user 'root'@'localhost'"
date: 2013-05-01
forum: General Help
---

### Post by Techguy718 on 2013-05-01
I'm not sure where to post this question, so I figured I might as well post it here. 

So here's the deal: I am installing/creating a web server in my tech class. 
As I try to install phpmyadmin, i get this annoying error:

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

I also get the same error when I try to reset the mysql password. 


ERROR 1045: Access denied for user: 'root@localhost' (Using password: NO)

Does anyone know how to fix this? I'd greatly appreciate it. Thanks

---

### Post by dino99 on 2013-05-01
[https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)

---

### Post by Techguy718 on 2013-05-02
I've tried this already, I've tried both methods. through the first method i get this error: 

Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql stop


Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop mysql

From there, I have no idea what to do. 
And when i try the second method, purging, I get this error: 

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using         
 &#9474; password: YES)


No matter what i do, i keep on getting the stupid error message. What should i do?

---

