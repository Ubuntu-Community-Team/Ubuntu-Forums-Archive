---
title: "apache issue"
date: 2008-06-02
forum: General Help
---

### Post by NightShade01 on 2008-06-02
So I setup my apache and it's been running fine for a few days.  then every few days I get this weird error and the server just dies and I end up having to revert to an earlier image (it's vmware).  I can't seem to figure out what causes the problem or how to fix it.  I have tried purging completely and then reinstalling but nothing.   The error is that when you try to start/stop/restart apache it says

apache2: Couldn't reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (no pid file) not running

Any else have this problem?

---

### Post by rampageoberon on 2008-06-02
> using 127.0.1.1 for ServerName

Shouldn't it be 127.0.0.1 or is that a typo?

Maybe try doing a force-reload instead

---

### Post by NightShade01 on 2008-06-02
no not a typo it should be 127.0.0.1 but I'm not sure what is causing it to change....

---

### Post by NightShade01 on 2008-06-03
So it seems that anytime I restart my machine it just does something to mess up the config files.  Apache never loads properly when I reboot, so i keep having to revert to a previous img.  Still no idea why it changes to 127.0.1.1......anyone?

---

