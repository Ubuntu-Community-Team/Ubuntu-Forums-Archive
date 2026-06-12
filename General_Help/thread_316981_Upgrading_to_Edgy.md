---
title: "Upgrading to Edgy"
date: 2006-12-11
forum: General Help
---

### Post by tjb891 on 2006-12-11
I want to upgrade from ubuntu 6.06 to ubuntu 6.10 without doing a clean install, is this possible or should i just burn all my personal files to a DVD and do a clean install?

---

### Post by Iarwain ben-adar on 2006-12-11
It is possible :D

Just change all instances of "dapper" with "edgy" in your /etc/apt/sources.list (withouth the "" ofcourse ;) )

Then type this
```
sudo aptitude update && sudo aptitude upgrade
```

An easier way would be to type
```
sudo aptitude dist-upgrade
```
(this way you don't have to edit your sources.list ;) )


Iarwain

---

### Post by hikaricore on 2006-12-11
p00f

---

### Post by Iarwain ben-adar on 2006-12-11
Ow,
sorry..
it's late here, and i was thinking of feisty :D

Edited ;)


Iarwain

---

### Post by hikaricore on 2006-12-11
> **Iarwain ben-adar said:**
> Ow,
sorry..
it's late here, and i was thinking of feisty :D

Edited ;)


Iarwain

Hehe it happens I was just like oh no... that's going to be very bad.

---

### Post by Iarwain ben-adar on 2006-12-11
.. Or alot of fun,
think about all the fixing to do :D

Thinking about it makes me wanna download Hoary (or Breezy) and update to Feisty..

Hmm, almost holidays.. :D


Iarwain

---

### Post by Ramses de Norre on 2006-12-11
> **Iarwain ben-adar said:**
> It is possible :D

Just change all instances of "dapper" with "edgy" in your /etc/apt/sources.list (withouth the "" ofcourse ;) )

Then type this
```
sudo aptitude update && sudo aptitude upgrade
```

An easier way would be to type
```
sudo aptitude dist-upgrade
```
(this way you don't have to edit your sources.list ;) )


Iarwain

You NEED to use dist-upgrade!! Otherwise you'll break your system big time. Dist-upgrade is the same as upgrade but allowed to delete obsolete packages and such.

So: first edit your sources and change all instances of dapper to edgy, and then run ```
sudo aptitude update && sudo aptitude dist-upgrade
```.
And I'd advice you to kill X and do this from a tty. And reboot you're machine when dist-upgrading is done.

---

### Post by renedox on 2006-12-11
What about from 5.10? At the time, I read from here that dist-upgrade breaks your system... How many people have had their system fail due to a dist-upgrade?

---

