---
title: "Newb cant lock out visitors in apache"
date: 2007-10-09
forum: General Help
---

### Post by posterboy on 2007-10-09
I USED to know how to do this! Failing miserably this time. I run xampp as my lampp stack here, and in httpd.conf, I have some lines of unwelcome guests. But, they continue right through the front door. Look:

# Controls who can get stuff from this server.
    #
    Order allow,deny
    deny from .telecomitalia.it .hinet.net .bezquint.net .steephost.com
    deny from .vtr.net .aafp.org .svservers.com .keymachine.de
    Allow from all
This isn't working, at all, what am I doing wrong? 

Thanks!

---

### Post by upbeat.linux on 2007-10-09
This may seem like a stupid question, but did you remember to restart apache after you made the configuration changes?

---

### Post by posterboy on 2007-10-09
Not at all a stupid question, but, yes, I did I restarted the lampp stack complete. 
Thank you.

---

### Post by upbeat.linux on 2007-10-09
Try this instead:

```
Order allow,deny
Allow from all
deny from .telecomitalia.it .hinet.net .bezquint.net .steephost.com
deny from .vtr.net .aafp.org .svservers.com .keymachine.de
```

---

### Post by posterboy on 2007-10-09
OK, thank you, I made those changes and restarted. May be some days before we will know anything. Should these lock-outs show up in error_log?

---

### Post by upbeat.linux on 2007-10-09
Correct me if I'm wrong, but they should be listed in access.log

Another word of advice, you many want to block these domain via your firewall.

---

