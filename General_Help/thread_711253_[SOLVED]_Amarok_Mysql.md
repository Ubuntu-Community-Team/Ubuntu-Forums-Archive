---
title: "[SOLVED] Amarok Mysql"
date: 2008-02-29
forum: General Help
---

### Post by ClearyA on 2008-02-29
I just set up mysql for amarok, and that all went down smoothly, however when i load amarok before i have time to load my database i get an error message "MySQL reported the following error:
Access denied for user 'amarok'@'localhost' (using password: YES)"
Any ideas?

---

### Post by flarkit on 2008-05-06
> **ClearyA said:**
> I just set up mysql for amarok, and that all went down smoothly, however when i load amarok before i have time to load my database i get an error message "MySQL reported the following error:
Access denied for user 'amarok'@'localhost' (using password: YES)"
Any ideas?

How was this solved, please?

**edit:** ahhhh... from [http://amarok.kde.org/wiki/MySQL_HowTo](http://amarok.kde.org/wiki/MySQL_HowTo), there is the line
> GRANT ALL ON amarok.* TO amarok@localhost IDENTIFIED BY 'PASSWORD_CHANGE_ME';

I used that exact password "PASSWORD_CHANGE_ME" in the Amarok settings, and it seems to have worked!

---

