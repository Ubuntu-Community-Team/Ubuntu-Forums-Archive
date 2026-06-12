---
title: "Localized Update Server"
date: 2008-05-21
forum: General Help
---

### Post by remush on 2008-05-21
I am about to install ubuntu + edubuntu onto 6 computers at our free pc training centre. I intend to install a general ubuntu install and then all the programs that come with edubuntu, what I would like to know is this : Can I download updates onto one computer and get the other 5 to get their updates from that one, thus saving us a lot of bandwidth, as we only get 50kbs max speed.

Thanks

---

### Post by Aearenda on 2008-05-21
I use apt-cacher for this purpose. [http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher](http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher) has a how-to.

EDIT: Also note the comment on that page to the effect that you can edit /etc/apt.conf to activate the cache on the clients, instead of changing each deb line in /etc/apt/sources.list:
edit apt.conf and add
Acquire::http::Proxy "http://repository-cache:3142";

---

