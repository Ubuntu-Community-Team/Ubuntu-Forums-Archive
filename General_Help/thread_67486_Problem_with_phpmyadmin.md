---
title: "Problem with phpmyadmin"
date: 2005-09-20
forum: General Help
---

### Post by ones on 2005-09-20
When I go to phpmyadmin, I put root and leave the password field in blank (as I read in other posts)

But I get this error:

> #2002 - The server is not responding (or the local MySQL server's socket is not correctly configured)

What's the problem?

I think mysql it's correctly installed, I went to /etc/mysql/my.cnf and I didn't see anything wrong.

I have installed PHP5, apache 2 (these are right because I tested with a page), phpmyadmin and also MySQL

Help plz  ](*,)

---

### Post by ones on 2005-09-21
No one knows about this?

Anyway, how can I be sure that mysql server it's running? (maybe it's that the problem)

---

### Post by dholwerda on 2006-02-25
i had a similar problem - something about mysql not allowing connections on hosts other than 127.0.0.1.  

Try changing your /etc/phpmyadmin/config.inc.php file to uncomment this line:
$cfg['Servers'][$i]['host']          = '127.0.0.1';

---

