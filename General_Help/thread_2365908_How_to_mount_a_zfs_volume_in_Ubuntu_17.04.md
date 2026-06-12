---
title: "How to mount a zfs volume in Ubuntu 17.04"
date: 2017-07-12
forum: General Help
---

### Post by sdy-zjx on 2017-07-12
Hi,there. I had a home server which runs freenas. Recently my server didn't work. I wanna copy my data to my computer, but when i run "zfs mount" , it said "[COLOR=#141414][FONT=rubik] [/FONT][/COLOR]filesystem cannot be mounted, unable to open the dataset ". How can I solve the problem? Thank you so much for your help.

---

### Post by ariek on 2017-07-15
First install the right packages to use zfs:
sudo apt install zfs: zfsutils-linux
then import the pool:
sudo zpool import

---

