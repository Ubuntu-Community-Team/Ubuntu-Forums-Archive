---
title: "Who's got ejabberd 1.1.2 (from repo) + jwchat + JabberHTTPbind +apache2 to work?"
date: 2008-01-15
forum: General Help
---

### Post by zakhooi on 2008-01-15
Hi,

I'm running ejabberd from repo (thats version 1.1.2) and I'd like to user jwchat ([http://jwchat.sourceforge.net/](http://jwchat.sourceforge.net/)).
In order to get that to work I have to use a servlet called JabberHTTPBind ([http://zeank.in-berlin.de/jhb/](http://zeank.in-berlin.de/jhb/)).
In order to run this servlet I had to install tomcat 5.5. (also from repo).

So far all fine.

I did all the configuration that's necessary (I read a lot, and I mean really a lot about how to configure this).
e.g.
[http://www.blochberger.de/en_jwchat_how_to.htm](http://www.blochberger.de/en_jwchat_how_to.htm)
[http://www.ejabberd.im/jwchat-localserver](http://www.ejabberd.im/jwchat-localserver)

However, I can't get jwchat to work.

ejabberd is fine, I can connect using a client like pidgin and also the webadmin works fine.
tomcat is fine, it's adminpage works, I deployed the jabberhttpbind servlet succesfully
apache2 works fine, the jwchat page shows up, proxysettings and rewrite settings are ok.
necessary modules within apache2 are running fine (mod_proxy, mod_proxy_http, mod_rewrite, mod_jk, etc...)

No matter what I try, jwchat can't connect succesfully to my jabber server

I know that ejabberd 2.0.0 beta has httpbind buildin but that is still an unstable version.

Therefor this is a call to the ones amonst you that have jwchat working succesfully on ejabberd 1.x

If so, could you please provide me a clear step-by-step howto since I'm flabbergasted by now.

Thanks in advance.

---

### Post by zakhooi on 2008-01-17
nobody?

---

### Post by zakhooi on 2008-01-18
bump

---

### Post by zakhooi on 2008-01-23
kick

---

### Post by Wobedraggled on 2008-02-27
I'd like to know this as well.

---

### Post by loulou2u on 2008-03-19
I am in the same boat but in my case the login button is greyed out and I'm not sure why. Also, does anyone know if it is a problem that my jabber chat server is not on the same server as my jwchat client?

Thanks

---

