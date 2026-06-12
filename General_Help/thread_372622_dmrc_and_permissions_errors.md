---
title: "dmrc and permissions errors"
date: 2007-02-28
forum: General Help
---

### Post by rito25 on 2007-02-28
Help. When ever I start up my computer after i log in i get a error says that .dmrc file permissions are wrong. I've tried  changing the permissions and they wont change. also I cant change my resolution. I'm running root and ubuntu 6.10.

---

### Post by rito25 on 2007-02-28
bump

---

### Post by bravemosquito on 2007-03-23
You must change the group of user back to that one when you created the user. For example when you create user 'X' the corresponding group must be 'X'

---

### Post by bodhi.zazen on 2007-03-23
file permissions, in a terminal: (use first set)

> 	sudo chmod 644 .dmrc
	sudo chown user_name .dmrc
	sudo chmod 755 /home/user_name
	sudo chown -R user_name /home/user_name

	OR, if that fails:

> 	sudo chown -R user_name /home/user_name 
	sudo chmod 755 /home/user_name
	sudo rm -rf /home/user_name/.dmrc

---

### Post by bravemosquito on 2007-03-24
> **bodhi.zazen said:**
> ...

This doesn't work every time. In about half (including me) of cases you did fresh install. But if u are lucky to save at 100% your data. After that you must only do the same things to return your configuration (for example install a game through the terminal) and HEADSHOT! - same error, same shi*. My cases are: on one machine with chmod/chown, on second with group permissions, on third with reinstall, on fourth with fresh install, on fifth changed the distro, on seventh double-kicked the pc :D , on eight tried to meditate and focus [-o< , on nineth deleted the /.dmrc file and that's the last nail on the coffin...

---

