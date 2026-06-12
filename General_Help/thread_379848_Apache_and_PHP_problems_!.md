---
title: "Apache and PHP problems !"
date: 2007-03-08
forum: General Help
---

### Post by sdil on 2007-03-08
When I open phpmyadmin, it ask me to save or open with other program. What must I do ?
 When I restart apache, it say this :

* Forcing reload of apache 2.0 web server...                                   apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ ok ]

Sorry for my english mistake.

---

### Post by Slojah on 2007-03-09
what does this return:

```

uname -a

```

---

### Post by muzzamo on 2007-03-24
I had a similar problem with this, in the end (after installing heaps of other packages so this may or may not help) my final command was 

""sudo apt-get install mysql-server libapache2-mod-auth-mysql php5-mysql"

**However, the most important thing is that if you are using firefox, clear cache ("clear private data") after each time you try something new. **

Otherwise firefox will continue trying to download the .php file as before, even though you may have fixed the problem.

---

