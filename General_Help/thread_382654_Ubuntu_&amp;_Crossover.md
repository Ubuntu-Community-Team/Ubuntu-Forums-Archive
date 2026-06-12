---
title: "Ubuntu &amp; Crossover"
date: 2007-03-12
forum: General Help
---

### Post by dgore on 2007-03-12
I installed Crossover on 6.10 this weekend.  Could only get it to install to my home folder.  According to instructions if I was logged in as root I would have had the option for it to be available for all users.  Using SUDO didn't work at all.  Got a message that it didn't have permissions to home folder.

I am new to Ubuntu.  is there another way to install as root besides SUDO?

Thanks

---

### Post by odysseus.lost on 2007-03-12
Well sudo should be executing as root. However, if you really want to logon as root
$ sudo su
OR
1. Create a password for root
  $ sudo passwd root
2. Then you can switch to root at will by su (rememer to provide here the root password and not the user's)


BTW as far as i remember cxoffice worked flawlessly on my u-6.06.

---

