---
title: "Can't su into root"
date: 2005-08-12
forum: General Help
---

### Post by koggo on 2005-08-12
I just installed my new Ubuntu system, i'm planning on using it as a webserver, and as I was trying to install XAMPP (Webserver package: [http://www.apachefriends.org](http://www.apachefriends.org)) and once I downloaded it, i went to su to install it and It said:

su: Authentication failure
Sorry.

I even tried resintalling Ubuntu and it still didnt work, is there a default password or something??

---

### Post by PeP on 2005-08-12
there is NO root account,
happily, the first user created has all the privileges enabled in sudo.

---

### Post by clapton on 2005-08-12
you haven't set the root user and pw.
you can use sudo with first user.
Or set a root 

sudo passwd root

---

### Post by Shwiing on 2005-08-15
This has happened to me before, you have to reset the root password its weird yes....

---

