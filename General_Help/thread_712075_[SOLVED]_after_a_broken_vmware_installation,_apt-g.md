---
title: "[SOLVED] after a broken vmware installation, apt-get fails"
date: 2008-03-01
forum: General Help
---

### Post by sadeghi on 2008-03-01
Hi
I'm newbie. I have a really confusing problem. I tired to install vmware in ubuntu, i made an ACE package in my Windows XP using vmware worksation and packaged my xp installation to use within ubuntu. after getting any kind of errors ( that made me search for solutions each time in forum ) i could not finish the installation of vmware.

Now the problem, each time that i try to use "apt-get" or "dkpg --conifgure -a" or any thing related to update some packages system invokes vmware configuration, instead of updating or getting packages from repository.

Now I'm really confused, cant update and cant get any packages.:confused:

any help is really appreciated.

Thanks

using ubuntu 7.10 on Dell inspiron 640m.

---

### Post by Glaxed on 2008-03-01
have you tried
```

sudo apt-get -f install
sudo apt-get update

```
?

---

### Post by sadeghi on 2008-03-01
Thanks, the problem solved with a system restart. It's newbie man!! ;-)

---

