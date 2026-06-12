---
title: "How to install VLC Media Player?"
date: 2017-04-25
forum: General Help
---

### Post by xipho2 on 2017-04-25
The "Ubuntu Software" asked for an Ubuntu One Account-why? I installed  it from the VLC website. What might be the problem doing so?

---

### Post by howefield on 2017-04-25
Because you are trying to download the snap version, look in the details section and it will likely say "daily" for the version. That is the snap version.

There is another package for VLC, in the traditional .deb format which is likely the one that you want ?

---

### Post by tripp98 on 2017-04-25
to install the easy way.

sudo apt install vlc

sudo - gives you rights to install
apt - program to install applications
install - command to use within apt
vlc - program to install

---

### Post by xipho2 on 2017-04-26
> **howefield said:**
> Because you are trying to download the snap version, look in the details section and it will likely say "daily" for the version. That is the snap version.

There is another package for VLC, in the traditional .deb format which is likely the one that you want ?

As I do not know the meaning of a snap version, daily or .deb, I cannot answer. I tried to install a common software via Ubuntu Software, that did not work.

---

### Post by xipho2 on 2017-04-26
Nice and informative reply-just one thing: What is "sudo apt-**get**" ...?

---

### Post by oldrocker99 on 2017-04-26
> **xipho2 said:**
> Nice and informative reply-just one thing: What is "sudo apt-**get**" ...?

Until 16.04, the standard command to deal with software packages was **apt-get**. It does still work, but has been supplanted with the **apt** command. The apt command has features that apt-get doesn't have.

---

