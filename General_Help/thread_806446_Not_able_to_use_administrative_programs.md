---
title: "Not able to use administrative programs"
date: 2008-05-24
forum: General Help
---

### Post by dayneman1 on 2008-05-24
When i click on the system menu then the administration menu and try to open any number of programs, such as software sources and synaptic package manager, I'm not getting the dialog for my password which is not letting the program run.  I'm able to open the any of the programs if i go through the terminal and use the sudo command (ex: sudo synaptic package manager).  Thanks for any help anyone is able to provide.

---

### Post by Steve413z on 2008-05-25
i am having the same problem, but only with the "users and groups" administrative utility

---

### Post by Steve413z on 2008-05-25
alright, i think i might have solved the problem

sudo usermod -G admin [YOUR USER NAME]
sudo usermod -G root [YOUR USER NAME]

restart x

---

### Post by dayneman1 on 2008-05-25
That wasn't it.  It actually removed the synaptic package manager and software sources.

---

### Post by Steve413z on 2008-05-25
crap!

that happened to me too, but it fixed it for me!

i hope you didn't mess with the /etc/sudoers file
if you did you are going to need to reboot into recovery mode and fix that file with the "visudo" command (and hopefully you know how to use vi)

---

### Post by aysiu on 2008-05-25
In the terminal, run the command ```
gksudo synaptic
``` If you get error messages, post them back here.

---

