---
title: "How to completely uninstall oracle java"
date: 2013-03-23
forum: General Help
---

### Post by livingdanger on 2013-03-23
I installed oracle for a bit because I thought I was having trouble with openjdk, after a bit of testing it turned out it wasn't openjdk so I switched back and un installed oracle but when I didit still left over the oracle console oracle, visualVM and two other oracle java related links I was just wonder how you get rid of these as well and what I did wrong.

Here's what I did, did I miss something?:

sudo rm /var/lib/dpkg/info/oracle-java7-installer*
sudo apt-get purge oracle-java7-installer*
sudo rm /etc/apt/sources.list.d/*java*
sudo apt-get update

---

