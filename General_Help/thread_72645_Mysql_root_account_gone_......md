---
title: "Mysql root account gone ....."
date: 2005-10-06
forum: General Help
---

### Post by dbee on 2005-10-06
I've managed to kill my admin account in mysql when I was playing around with my webmin installation. The admin account is deleted completely ...

I have tried resetting the password but that didnt work (obviously). I also can't use my one remaining account to escalate my privileges or setup new users. My only remaining account is not able to access the mysql table. I also reinstalled mysql but strangely I get the exact same user configuration upon reinstallation ... even when I remove mysql completely with syanptic. 

I find this strange, as the mysql conf (my.cnf) file doesn't store any user settings, I don't see how the user config remains from one install to the next.

Anybody got any suggestions on what I should do ???

Thanks

---

### Post by lonetree on 2006-08-30
Hi dbee, 

just saw your thread today after breaking my mysql root account. ave you got yours sorted out? I just wonder why can't I get the root account back, even if I uninstall mysql-server thru apt-get remove.

Does anyone has any suggestion on how to completely remove mysql and do a clean installation?

Thanks.

Regards,

---

### Post by nolanjurgens on 2006-09-02
If you use "apt-get remove --purge packagename", all of the configuration files are removed as well. I'm not sure if it will fix your problem, but it's worth a shot.

---

### Post by lonetree on 2006-09-05
Hi nolanjurgens,

thanks for your reply. Yes, I found the same command somewhere in this forum and fix the problem. Really thank you for this reply too. What i did was simply purge all packages with regards to MySql since I haven't even done anything to it when it was first installed. Then, I do aclean installation using apt-get install mysql-server and all are back to normal.

Regards,

---

