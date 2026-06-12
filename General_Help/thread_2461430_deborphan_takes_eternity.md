---
title: "deborphan takes eternity"
date: 2021-04-30
forum: General Help
---

### Post by yairz830 on 2021-04-30
Hi

Help ! I'm a newbie :)

In order to free some space I run this command on my ubuntu 20.04 :

$ deborphan | xargs sudo apt --purge remove

(I read somewhere that it will remove all orphaned packages)

but it's running for over 30 minutes now !

after hitting 'Yes' I get this loop:   ( what should I do? )

[IMG]https://i.ibb.co/b5VPhxL/scr4.png[/IMG]

---

### Post by dino99 on 2021-04-30
Better using commands into a terminal:
> sudo apt clean
sudo apt autoclean
sudo apt autoremove

or install and use "bleachbit" as root but carefully select the jobs you want/need to run

---

