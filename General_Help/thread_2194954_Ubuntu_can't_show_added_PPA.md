---
title: "Ubuntu can't show added PPA"
date: 2013-12-21
forum: General Help
---

### Post by ubunet on 2013-12-21
Hi,

I update my system and added the qBittorrent ppa but in **Synaptic** or **Terminal** I can't install the lastest package.

```
sudo add-apt-repository -y ppa:hydr0g3n/qbittorrent-stable && sudo apt-get update && sudo apt-get upgrade
```

My qBittorrent is 3.0.11 running in **Xubuntu Saucy** 13.10 x32 bits.

[B]The system can't see the ppa!

[/B]

---

### Post by Toz on 2013-12-21
Also run:
```
sudo apt-get upgrade
```
...to actually upgrade packages.

---

### Post by ubunet on 2013-12-21
> **Toz said:**
> Also run:
```
sudo apt-get upgrade
```
...to actually upgrade packages.

Doesn't work. I do it!

---

### Post by Toz on 2013-12-21
What version of Ubuntu do you use?

What does the following command show:
```
apt-cache policy qbittorrent
```

---

### Post by monkeybrain20122 on 2013-12-21
There is nothing wrong with your system. There is no saucy package in the ppa. They are not able to build the saucy package, go to the launchpad page of the ppa, click details and see for yourself. 
Also,[https://github.com/qbittorrent/qBittorrent/issues/1061](https://github.com/qbittorrent/qBittorrent/issues/1061) (ticket closed 25 days ago but still no new build)

There is another ppa with qbittorrent 3.1.3 [https://launchpad.net/~anton50489/+archive/test/+index?batch=75&direction=backwards&memo=150&start=75](https://launchpad.net/~anton50489/+archive/test/+index?batch=75&direction=backwards&memo=150&start=75) 
Use at your own risk (it may update some dependencies which may mess things up  elsewhere) and disable it after you install qbittorrent as it has a lot of packages you probably don't want to upgrade.

---

### Post by mc4man on 2013-12-21
Trusty(14.04) is not that far advanced from 13.10 & does have the current. It's likely that it will work ok in 13.10.
To try  out
go here, pick/click on  arch, download the .deb
Then r. click on the dl'ed .deb > "Open with Ubuntu Software Center" & see...
[http://packages.ubuntu.com/trusty/qbittorrent](http://packages.ubuntu.com/trusty/qbittorrent)

---

### Post by ubunet on 2013-12-21
> **monkeybrain20122 said:**
> There is nothing wrong with your system. There is no saucy package in the ppa. They are not able to build the saucy package, go to the launchpad page of the ppa, click details and see for yourself. 
Also,[https://github.com/qbittorrent/qBittorrent/issues/1061](https://github.com/qbittorrent/qBittorrent/issues/1061) (ticket closed 25 days ago but still no new build)

There is another ppa with qbittorrent 3.1.3 [https://launchpad.net/~anton50489/+archive/test/+index?batch=75&direction=backwards&memo=150&start=75](https://launchpad.net/~anton50489/+archive/test/+index?batch=75&direction=backwards&memo=150&start=75) 
Use at your own risk (it may update some dependencies which may mess things up  elsewhere) and disable it after you install qbittorrent as it has a lot of packages you probably don't want to upgrade.

I **didn't** know this problem.

Thank you for reply.

---

