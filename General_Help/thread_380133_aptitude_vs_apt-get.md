---
title: "aptitude vs apt-get"
date: 2007-03-09
forum: General Help
---

### Post by rjfioravanti on 2007-03-09
What is the difference between using aptitude and apt-get to do installs, upgrades, removals etc

---

### Post by Kateikyoushi on 2007-03-09
Aptitude is a frontend for apt-get introducing new funcionality and better package handling. You can find a real life comparision here. [LINK]("http://www.psychocats.net/ubuntu/aptitude")

---

### Post by rjfioravanti on 2007-03-09
I am asking because I was worried about removing with apt-get and not cleaning up unused dependencies. Someone told me I could remove unused dependencies if I used aptitude commands, but not if I installed with apt-get

so is that the only different, apt-get doesnt clean up unused dependencies?

but now it supports apt-get autoremove, so now with that do they have equal functionality?

I wanted to completely remove ubuntu stuff and install xubuntu

so can I do

```

sudo apt-get autoremove ubuntu-desktop
sudo apt-get install xubuntu-desktop

```

?

---

