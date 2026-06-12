---
title: "Help with chown"
date: 2008-06-01
forum: General Help
---

### Post by Tagati on 2008-06-01
Iam trying to change the MYSQL datadir and when i use chown -R mysql:mysql /mnt/users/* i dont get any output and when i change the my.cnf to point to the new dir and restart mysql i get a fail, iam folling this [http://www.debianadmin.com/mysql-database-server-installation-and-configuration-in-ubuntu.html](http://www.debianadmin.com/mysql-database-server-installation-and-configuration-in-ubuntu.html)
has any one any ideas where iam going wrong please ? Thanks.

---

### Post by x1a4 on 2008-06-01
Hi,

Please provide more information.  What's the error you're getting?  Did you move the files from /var/lib/mysql/ (except for ib_arch_log_0000000000, ib_logfile0 etc) to /mnt/users/ (I assume that's the new data directory you want) **before** changing ownership?  Is /mnt/users/ mounted (I assume it's another partition)?  What do you mean you restarted MySQL?  You should stop it, make the changes then start it again--**not** keep it running, make changes and restart.

---

### Post by Tagati on 2008-06-02
Thanks for the reply :-) i think i know where i was going wrong, i was moving the hole mysql file over when i should of just copped the mysql file that is in the mysql file and not the hole lot :-( as you said in your post, thanks again, hope thats going to work now.

---

### Post by Tagati on 2008-06-02
Ive posted a new thread about this as this one is a little of the subject now, please remove this one if need be, thanks.

---

