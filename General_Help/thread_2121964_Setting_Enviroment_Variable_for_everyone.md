---
title: "Setting Enviroment Variable for everyone"
date: 2013-03-03
forum: General Help
---

### Post by myforwik on 2013-03-03
I tried to set an enviroment variable for everyone by putting it in /etc/enviroment

However, when users bring up terminal, its not defined. It is defined if they do a root console with sudo su.

I have a program that anyone can run that needs an enviroment variable set to a certain value, how can I do it?

(Running ubuntu 12.04 LTS)

---

### Post by thnewguy on 2013-03-03
I suspect the file you are looking for is either /etc/profile or /etc/bash.bashrc, assuming your users are all using the default BASH shell. For details on the shell and the above files check out the bash man page by running "man bash".

---

