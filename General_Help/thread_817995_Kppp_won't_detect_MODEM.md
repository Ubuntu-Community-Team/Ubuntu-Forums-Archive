---
title: "Kppp won't detect MODEM"
date: 2008-06-04
forum: General Help
---

### Post by Goldpin on 2008-06-04
I've just installed Kppp because I have to reboot my system every time I use gnome ppp to connect and then reconnect after ending the first connection. Kppp worked fine the first time I used it, but after doing a reinstall, when I query the modem, it either won't detect it or says something like "can't find lock file".  The last time in installed Kppp, I downloaded it from the net, so the dependencies should all be satisfied.


I'd really appreciate some ideas on this.  Thanks in advance.

---

### Post by ardvark71 on 2008-06-04
> **Goldpin said:**
> Kppp worked fine the first time I used it, but after doing a reinstall, when I query the modem, it either won't detect it or says something like "can't find lock file". 


Hi...

I never was able to get KPPP to work, no matter what I did or tried, so you're definately ahead of me. ;)

Although not directly related to your problem this site might provide some insight....

[http://www.querycat.com/faq/b8cf5481b46069e937031e23908ba562](http://www.querycat.com/faq/b8cf5481b46069e937031e23908ba562)

You can also use wvdial in the meantime as an alternative to getting online. Be sure to run wvdial config tool first and then run konqueror in super user mode to edit the config file to include your dial-up number, username and password. If there are any problems connecting, add the line "check carrier = no"

You can view the wvdial.conf man page here...

[http://linux.die.net/man/5/wvdial.conf](http://linux.die.net/man/5/wvdial.conf)

Best Regards...

---

