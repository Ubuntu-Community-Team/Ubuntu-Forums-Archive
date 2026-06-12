---
title: "Urgent help needed configuring offline update"
date: 2013-06-12
forum: General Help
---

### Post by boserahul on 2013-06-12
Hi Everyone,

Urrgent help needed in configuration offilne repository for 10.04 for my office environment. Already done by 90% of total work. Infact other ubuntu client system are getting updated from the newly created from the new created Offline Repository server. But Stuck on one stage.

Already Run apt-mirror command downloaded 81 GB files In total, symbolic link already created, apache 2 already installed. But the problem is The Canonical partner repo is not available. We had to download some file flash properties gtk, acroread read which are present in the partner Repository. Even i already dumped the partner repo as well. I can see the files manually like flash-gtk, acroread in my locally created repo. But somehow those not able to download. Here is the repo list in my apt-mirror config.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-proposed main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-backports main restricted universe multiverse

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security main restricted universe multiv$
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main restricted universe multive$
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-proposed main restricted universe multiv$
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-backports main restricted universe multi$

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

Here is The Client system sources.list

deb [http://172.29.18.131/ubuntu](http://172.29.18.131/ubuntu) lucid main restricted universe multiverse
deb [http://172.29.18.131/ubuntu](http://172.29.18.131/ubuntu) lucid-updates main restricted universe multiverse
deb [http://172.29.18.131/ubuntu](http://172.29.18.131/ubuntu) lucid-security main restricted universe multiverse
deb [http://172.29.18.131/ubuntu](http://172.29.18.131/ubuntu) lucid-proposed main restricted universe multiverse
deb [http://172.29.18.131/ubuntu](http://172.29.18.131/ubuntu) lucid-backports main restricted universe multiverse

deb-src [http://172.29.18.131/ubuntu](http://172.29.18.131/ubuntu) lucid main restricted universe multiverse
deb-src [http://172.29.18.131/ubuntu](http://172.29.18.131/ubuntu) lucid-updates main restricted universe multiverse
deb-src [http://172.29.18.131/ubuntu](http://172.29.18.131/ubuntu) lucid-security main restricted universe multiverse
deb-src [http://172.29.18.131/ubuntu](http://172.29.18.131/ubuntu) lucid-proposed main restricted universe multiverse
deb-src [http://172.29.18.131/ubuntu](http://172.29.18.131/ubuntu) lucid-backports main restricted universe multiverse

deb [http://172.29.18.131/ubuntu](http://172.29.18.131/ubuntu) lucid partner
deb-src [http://172.29.18.131/ubuntu](http://172.29.18.131/ubuntu) lucid partner

Need ur urgent help on this

---

### Post by gordintoronto on 2013-06-12
Ubuntu 10.04 Desktop reached end of support two months ago. A few updates which are relevant to Ubuntu Server might trickle through, but you are facing security issues, among other things.

You effort would provide better results if you created a plan for moving to a current version of Linux. Xubuntu 12.04 might fill the bill, if you don't want to train people on using Unity.

---

