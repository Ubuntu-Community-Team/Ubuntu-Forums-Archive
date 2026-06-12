---
title: "ssh connection problems permission denied."
date: 2007-05-06
forum: General Help
---

### Post by beachreader on 2007-05-06
When I try to ssh <hostname> I get an error " name or service not known"

when I try ssh <ip adress> i get : password : ( i only have one password for both machines) permission denied please try again.

finally when I try connection to server : it keeps asking me for my password. Everytime I input my password, it comes up again requesting my passwork on going....


please any suggestions...this is terrible problem...thanks

---

### Post by Buster222 on 2007-05-06
I presume that you are ssh-ing into an Ubumtu machine. If so, them try:
ssh yourusername@hostname
hostname must of cause appear in /etc/hosts in the machine you are ssh-ing from. If it doen't then try
ssh yourudername@IP-address

---

