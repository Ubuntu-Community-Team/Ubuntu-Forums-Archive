---
title: "Trying to enable mod_rewrite on LAMP server"
date: 2007-11-30
forum: General Help
---

### Post by allspiritseve on 2007-11-30
Hi,

I am running Apache 2.2.4 on my laptop, and would like to use mod_rewrite. I have configured this before in windows installs, but this time the .conf files are way different. At this point my server does not recognize .htaccess files, and I'm not sure exactly how to fix that.  Do I edit apache2.conf? Httpd.conf? /sites-enabled/000-default?

Thanks,

Cory

---

### Post by WearZeeP on 2007-11-30
In default apache installs on Ubuntu, overriding the default settings (with .htaccess) isn't allowed, so you need to change this.
I had the exact same problem when i did it, but now I forgot how to change it, but i quick Google search came up with this:
[http://josh.st/blog/2005/03/06/ubuntu-apache-and-making-mod_rewrite-happy]("http://josh.st/blog/2005/03/06/ubuntu-apache-and-making-mod_rewrite-happy")

---

