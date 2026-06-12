---
title: "Software-updater doesn't ask me for root password"
date: 2013-02-27
forum: General Help
---

### Post by GnuKian on 2013-02-27
When I get a prompt to install new updates, it usually doesn't want any password: when I click "Install", it automatically tries to download and install them. this often happens for security updates.
why ubuntu doesn't ask me for my root password? Is this safe?


My Ubuntu: 12.10 (updated)

---

### Post by mörgæs on 2013-02-27
Yes. 

It was changed one or two releases ago. The reason is that asking for a password might keep some users away from installing. 

Only when a new kernel is offered one has to give the password. A new kernel is a more fundamental change to the system and is not considered a normal update. 

You might notice that **sudo apt-get upgrade** does not apply a new kernel, but **sudo apt-get dist-upgrade** does. It's the same distinction.

---

