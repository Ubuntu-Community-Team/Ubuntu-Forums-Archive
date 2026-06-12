---
title: "Mysql - grant access to local computer"
date: 2019-05-03
forum: General Help
---

### Post by bill-lancaster on 2019-05-03
I have been running mysql on my Kubuntu machine for a long time.
I now have a second Kubuntu machine on my LAN.
Mysql is installed on a computer I'll call 'Vostro',  the second machine ('Compaq') is a fresh Kubuntu install.
Both are running Kubuntu 18.04
How can I access mysql databases on 'Vostro' from 'Compaq'?

---

### Post by Tadaen_Sylvermane on 2019-05-03
Configure mysql to be open to lan. I set my bind address to 0.0.0.0. Static ip on mysql server machine, connect, profit!

---

### Post by SeijiSensei on 2019-05-03
MySQL accounts are all of the form 'user'@'hostname'. You may need to add that user to the server if connecting from another location.

---

### Post by bill-lancaster on 2019-05-09
Thanks for the advice, my second machine won't be available for a while but I looking forward to implementing the advice soon.

---

