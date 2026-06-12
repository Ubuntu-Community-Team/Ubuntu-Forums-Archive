---
title: "How to install Infinality on 17.10? fontconfig-infinality not found in Ubuntu 17.10"
date: 2018-02-16
forum: General Help
---

### Post by wahidrahim on 2018-02-16
Hello, I am a long time user of Infinality for font rendering.

After I upgraded to 17.10, I tried to install Infinality as I always do:

```

sudo add-apt-repository ppa:no1wantdthisname/ppa
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install fontconfig-infinality

```

But [FONT=courier new]fontconfig-infinality[/FONT] is not found.

I am wondering how to install Infinality in Ubuntu 17.10

---

### Post by epichinuq on 2018-06-15
You can install it via .deb package

> 
cd /tmp
wget [https://launchpad.net/~no1wantdthisname/+archive/ubuntu/ppa/+files/fontconfig-infinality_20130104-0ubuntu0ppa1_all.deb](https://launchpad.net/~no1wantdthisname/+archive/ubuntu/ppa/+files/fontconfig-infinality_20130104-0ubuntu0ppa1_all.deb)
sudo dpkg -i fontconfig-infinality_20130104-0ubuntu0ppa1_all.deb 
sudo bash /etc/fonts/infinality/infctl.sh setstyle


Tested in Ubuntu 18.

---

