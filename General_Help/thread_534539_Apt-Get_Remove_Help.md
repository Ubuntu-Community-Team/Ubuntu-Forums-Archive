---
title: "Apt-Get Remove Help?"
date: 2007-08-25
forum: General Help
---

### Post by BrandonIngham on 2007-08-25
I tried to remove sendmail and mysql completely because i accidentily deleted the mysql root user and sendmail is messed up.
sudo apt-get remove --purge sendmail
sudo apt-get remove --purge mysql-server

And they havent gone. It says they have when i try to uninstall them again but i can still see them in webmin and they still load up when i boot the pc.
Anyone help please?

---

### Post by aJayRoo on 2007-08-25
The reason for this behaviour is that they are meta packages. They depend upon a particular version (usually the latest) of the package. In the case of mysql server the package 'mysql-server' is a meta package that depends on 'mysql-server-5.0'. If you want to remove mysql-server you need to remove the actual package and not just the meta package as it is often safe to remove meta packages after they have done their job. To put it simply the command you require is:
```
sudo apt-get remove --purge mysql-server-5.0
```
I'm not sure if sendmail is the same situation but I would guess that it is. I hope my explanation was not too hard to understand!

---

