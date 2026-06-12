---
title: "MySQL server's socket is not correctly configured"
date: 2007-05-04
forum: General Help
---

### Post by useLinux, on 2007-05-04
I tried this before in the begginer talk but im not sure its supposed to go there now. So i decided to post it here too.

After everything for my server works, and i installed, this comes up when i try to login to phpmyadmin or do anything in terminal with the database.

Error
#2002 - The server is not responding (or the local MySQL server's socket is not correctly configured)

It was working before, becuase i logged into phpmyadmin and created databases (testing it) then when i tried it again like 4 - 5 days later it just didnt work. :S

Ive tried looking at like FAQ's and community documentation but i cant seem to be able to fix it. Any ideas?

[Thanks for all those who help]

---

### Post by natbudin on 2007-05-11
It's hard to diagnose this problem without knowing more.  Could you post the contents of your /var/log/mysql.log and /var/log/mysql.err files?

---

