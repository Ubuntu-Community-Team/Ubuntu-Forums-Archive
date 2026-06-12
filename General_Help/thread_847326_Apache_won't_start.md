---
title: "Apache won't start"
date: 2008-07-02
forum: General Help
---

### Post by Spudinski on 2008-07-02
I wanted to change a few settings in the configuration of apache, this is after I have configured it before.
Everything was working perfectly as I wanted it to.

I wanted to install mod_rewrite and followed an online guide: [http://www.huanix.com/2007/04/18/mod_rewrite-for-apache2-in-ubuntu-feisty-fawn-704/](http://www.huanix.com/2007/04/18/mod_rewrite-for-apache2-in-ubuntu-feisty-fawn-704/)
I'm currently running Ubuntu as well.
After the installation, Apache didn't seem to start, it gives no startup errors, and a syntax check also produces no errors.
I have tried to backtrack my steps and uninstall it, but it doesn't seem to work.

Though, the startup process reports to be valid, yet the server is not started.
```
root@www:/# /etc/init.d/apache2 start
 * Starting web server apache2                                           [ OK ]

```

Seems stupid that a single mod would be this much trouble to install and configure.

---

### Post by HalPomeranz on 2008-07-02
Anything in /var/log/apache2/error.log?

---

