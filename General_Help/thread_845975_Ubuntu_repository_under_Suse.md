---
title: "Ubuntu repository under Suse"
date: 2008-07-01
forum: General Help
---

### Post by swisslink on 2008-07-01
Hi all,

I need to install a repository Ubuntu under Suse SLE10. I need Suse because the people  must have an access to Novell ressources and Suse is the officially Linux distribution in my company. 

Someone has an idea to do this ?

Thank you

:D

---

### Post by justleen on 2008-07-01
suse is not debian based, and cannot handle .deb files nativly (suse is rpm based).. you could convert them with "alien", if need be...

---

### Post by swisslink on 2008-07-01
Yes, I know that, but I would setup my /etc/apt/sources.list repository to go to my Suse server. I setup already a repository with Ubuntu, it's a web server and a big disk space... I was thinking that it possible to implement the same thing with Suse... The Suse server will just download all night the new deb packages and the Ubuntu client will download the deb file on this server when I make an apt-get install by example...

---

### Post by justleen on 2008-07-01
so, you want your suse box to act as a apt-repository?

---

### Post by swisslink on 2008-07-01
Yes !

Sorry for my poor english... :(

---

### Post by justleen on 2008-07-01
have a look at [http://apt-mirror.sourceforge.net/](http://apt-mirror.sourceforge.net/)
the source is on the download page as well, you should be able te get it up and running with that

---

### Post by swisslink on 2008-07-01
I will try.

Thank you !

---

