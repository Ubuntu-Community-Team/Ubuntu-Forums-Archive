---
title: "FTP Help."
date: 2007-05-04
forum: General Help
---

### Post by mattc908 on 2007-05-04
On Ubuntu Feisty Fawn Server i'm trying to install ProFtpd on it. I did it sucsessfuly but when I try and start it says: 

ProFTPd warning: cannot start neither in standalone nor in inetd/xinetd mode. Check your configuration.
 
Any Ideas?

---

### Post by 505 on 2007-05-04
Check /etc/proftpd/proftpd.conf and look for the setting ServerType. Mine is set to 'standalone'. The other option is 'inetd'

---

### Post by danbar on 2007-05-07
I don't know if I have an FTP problem or network problem.  I was using FTP add on on Firefox to connect to my satellite dreambox.  Now since I installed the latest ubuntu it cannot connect anymore.  Do I have to use the FTP which comes with Feisty or maybe it closes the ports for security reasons?

---

