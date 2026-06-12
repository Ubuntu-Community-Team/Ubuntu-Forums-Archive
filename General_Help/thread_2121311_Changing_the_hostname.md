---
title: "Changing the hostname"
date: 2013-03-01
forum: General Help
---

### Post by rmcellig on 2013-03-01
I need to change the hostname on my Lubuntu 12.04 computer. What I did was go into the hostname file located in /etc and change the hostname to something else. I get an unable to resole host mynewhostname.

 I saved the file and rebooted. Is there anything else I need to do like change the name some place else? The reason I ask is because the Samba share I set up on my Lubuntu machine is showing up on other machines on my LAN but I can't mount the share with the password I set.

I have a feeling I have to change the hostname somewhere else, but I can't remember where.

---

### Post by The Cog on 2013-03-01
Yes. 
You need to edit /etc/hosts as well so that it matches /etc/hostname.

---

### Post by rmcellig on 2013-03-01
Thanks for jogging my memory :)

---

