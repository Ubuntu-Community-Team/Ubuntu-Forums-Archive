---
title: "MOTD not displaying with LDAP login"
date: 2022-10-07
forum: General Help
---

### Post by bazzybtec on 2022-10-07
I have motd being pushed to ubuntu servers in my environment this part is working normally and when logging in with local accounts it displays motd however when logging in with an LDAP authenticated account even if a home directory is created it will not display the motd


in the sshd_config

UsePAM yes
PrintMotd yes
are set 

What can cause this message not to display under LDAP authenticated accounts?

---

