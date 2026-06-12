---
title: "Mint 20.2 and Xubuntu 19.10 and ZFS home not mounting"
date: 2021-08-02
forum: General Help
---

### Post by maurice-volaski on 2021-08-02
I have Mint 20.2 and Xubuntu 19.10 installations with ZFS showing the same behavior in that every once in a while, the home pool “forgets” to mount, so the user can’t login. They keep rebooting, and eventually it remembers to mount. 

Is this a known bug?

---

### Post by guiverc on 2021-08-02
Given Ubuntu 19.10 & all *flavors* [reached EOL more than a year ago]("https://fridge.ubuntu.com/2020/07/17/ubuntu-19-10-eoan-ermine-end-of-life-reached-on-july-17-2020/"), issues that exist now are no longer monitored or patched, however I'm not aware of any such issues existing more than a year ago when it reached it's *end-of-life*. 

 (ZFS was still *experimental* in 2019)

---

### Post by sudodus on 2021-08-03
I recommend that you

- backup your personal data
- make a fresh installation of Xubuntu **20.04.x LTS**
- restore the backed up data to the freshly installed system.

If you want to test the newest released Ubuntu version of ZFS, you can install Xubuntu **21.04**. You can even try the [developing version 'Impish'](http://iso.qa.ubuntu.com/qatracker/milestones/424/builds/234493/downloads) to be released as 21.10 in October (but there are bugs and can be new bugs, so it can be a bumpy road).

---

