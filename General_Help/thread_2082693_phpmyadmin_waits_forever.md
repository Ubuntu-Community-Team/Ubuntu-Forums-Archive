---
title: "phpmyadmin waits forever"
date: 2012-11-10
forum: General Help
---

### Post by ELMIT on 2012-11-10
Today on one of my servers phpmyadmin got mad:

I cannot login as root or as user. In both cases the browser shows:

"Waiting for <Servername>"

I restarted mysql already. I tested apps using the databank and I inserted the database I needed from the command line. Database works, ... so something got wrong with phpmyadmin.

Any ideas?

---

### Post by COMECON on 2012-11-10
Are you using Apache and MySQL and manually installed phpmyadmin, or are you using some LAMP suite?

---

### Post by ELMIT on 2012-11-10
I was thinking on restarting mysql but did not think to restart apache. That fixed it, ....

---

