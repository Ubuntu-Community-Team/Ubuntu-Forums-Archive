---
title: "lubuntu 12.04to12.10, installed programs"
date: 2012-10-18
forum: General Help
---

### Post by saltcushy on 2012-10-18
When I updated the lubuntu to 12.04 I lost a installed a programs and packages.So update to 12.10  will kill   a installations or not?

---

### Post by Cheesemill on 2012-10-18
Upgrading to a new version of Ubuntu shouldn't ever remove any of your applications.

What did you upgrade from last time?

---

### Post by saltcushy on 2012-10-18
I forgoten add that Lost it's the List  a installations

---

### Post by vasa1 on 2012-10-18
> **saltcushy said:**
> I forgoten add that Lost it's the List  a installations
I'm not sure I understand correctly, but if you want a list of software installed before you move from 12.04 to 12.10, you could run
```
dpkg --get-selections > installed-software
```
from a terminal and save the file called "installed-software" on another device altogether. That way, you'll have a list of software you have in 12.04.

But as Cheesemill said:> Upgrading to a new version of Ubuntu shouldn't ever remove any of your applications

---

### Post by saltcushy on 2012-10-19
@vasa1, so mean your command save direct connection files and apt(Synaptic menager),right?

---

### Post by vasa1 on 2012-10-19
> **saltcushy said:**
> @vasa1, so mean your command save direct connection files and apt(Synaptic menager),right?
Sorry!
The command just creates a file that lists the software on your computer at the time you run the command.
Here's a little bit:
```
accountsservice					install
ace-of-penguins					deinstall
acl						install
adduser						install
alsa-base					install
alsa-utils					install
anacron						install
app-install-data				install
apparmor					install
apport						install
apport-gtk					install
apt						install
apt-fast					install
apt-transport-https				install
apt-utils					install
aptdaemon					install
aptdaemon-data					install
aria2						install
...

```

---

### Post by firekage on 2012-11-03
> **vasa1 said:**
> I'm not sure I understand correctly, but if you want a list of software installed before you move from 12.04 to 12.10, you could run
```
dpkg --get-selections > installed-software
```from a terminal and save the file called "installed-software" on another device altogether. That way, you'll have a list of software you have in 12.04.

But as Cheesemill said:

BTW - could You explain, steb by step, what to do in "fresh" system with exported list from dpkg --get-selections? 

I would like to install all software, that i have in 12.04, that is with me even from 11.10, so, i should export it with dpkg --get-selections > packages.txt, and what to do from here on second system?


Big thanks.

---

