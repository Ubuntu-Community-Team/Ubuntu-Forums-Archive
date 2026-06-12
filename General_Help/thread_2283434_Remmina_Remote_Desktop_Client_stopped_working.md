---
title: "Remmina Remote Desktop Client stopped working"
date: 2015-06-22
forum: General Help
---

### Post by elim-qiu on 2015-06-22
I found Remmina Remote Desktop Client stopped working for some reason.

I've a static IP associated with a domain name for a win7 box that I can still control it remotely via iPad/Smart phone. I also installed Remmina Remote Desktop Client on my ubuntu 14.04 laptop(latitude) that worked just fine sometime before. 

But it simply saying "Unable to connect to RDP server mydomainName.net".

Uninstall and Reinstall it, still not working. Any ideas?

Thanks

---

### Post by elim-qiu on 2015-06-22
Just tried the same app on ubuntu 13.10, works fine. So how to fix it on 14.04?

---

### Post by elim-qiu on 2015-06-22
I found that RDT (ubuntu 14.04) is working if I set the connection with server's local IP instead of domain name. While using domain name is fine on 13.10.

So it's something about security measure... But what should I do if I'm away from local network?

---

### Post by postoffice-z on 2015-06-22
I have experienced the same problem in the last few days.  I resolved it by clearing the host entry from ~/.freerdp/known_hosts

---

### Post by jamesisin on 2015-06-22
You get no errors while running Remina?

Can you ping the machine by name from the 14.04 machine?

---

### Post by elim-qiu on 2015-06-23
Thanks a lot postoffice-z. That's it! 
I deleted the record there and add my domain as new server with Remmina RTD client. It worked right away!

---

### Post by elim-qiu on 2015-06-23
No errors runing Remina.  Guess the connection certificate expired....

---

### Post by jamesisin on 2015-06-24
Or the IP address changed.  That will cause it to fail as well.

---

