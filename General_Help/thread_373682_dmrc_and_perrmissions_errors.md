---
title: "dmrc and perrmissions errors"
date: 2007-03-01
forum: General Help
---

### Post by rito25 on 2007-03-01
Help. When ever I start up my computer after i log in i get a error says that .dmrc file permissions are wrong. I've tried changing the permissions and they wont change. also I cant change my resolution. I'm running root and ubuntu 6.10.

---

### Post by bodhi.zazen on 2007-03-01
> **rito25 said:**
> Help. When ever I start up my computer after i log in i get a error says that .dmrc file permissions are wrong. I've tried changing the permissions and they wont change. also I cant change my resolution. I'm running root and ubuntu 6.10.

Tisk tisk running X as root indeed ...

At any rate, to fix try this :

> 	sudo chmod 644 .dmrc
	sudo chown user_name .dmrc
	sudo chmod 755 /home/user_name
	sudo chown -R user_name /home/user_name

	OR, if that fails:

> 	sudo chown -R user_name /home/user_name 
	sudo chmod 755 /home/user_name
	sudo rm -rf /home/user_name/.dmrc

Where  user_name = your log-in name :p

---

