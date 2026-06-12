---
title: "Upgrading and compiling..."
date: 2007-09-06
forum: General Help
---

### Post by CoriolisSTORM on 2007-09-06
Alright ladies and gents, I'm considering upgrading Dapper to the newest version (Edgy I think?)  Is it possible for me to do so from the apt-get type deal or do I need to download the CD and do it that way?  Is it possible that it could break my wireless card?  I have just gotten it to working over 3 weeks ago and don't wish to go through the pain of getting it back working again.  How would I do this?
Also, I'm always looking for performance enhancements, and am running the default kernel now.  I have an AMD Athlon XP 2800+ and since it was a K7 chip, will I see any benefits of using a K7 kernel?  Can I just use synaptic or something to get that installed? How to do it would be great.   As you can see, I still have a lot to learn.  Thank you for your time.

---

### Post by apetresc on 2007-09-07
Hello, Coriolis :) You do *not* need to reinstall Ubuntu to update it; it can be updated entirely through apt. The newest version is Feisty, not Edgy, though it may be a good idea to first upgrade to edgy, then once that has succeeded, update to Feisty. The process is simple.

1) Open up the file /etc/apt/sources.list as root (with sudo). Replace ALL occurrences of the word "dapper" with the word "edgy"
2) Run ```
sudo apt-get update
```
3) Run ```
sudo apt-get dist-upgrade
```
4) Reboot
5) Repeat these steps, except replace "edgy" with "feisty" this time

That will be all, good luck! :)

---

### Post by rsambuca on 2007-09-07
Actually, that is not the Supported method of upgrading from Dapper to Edgy.  I suggest you follow the instructions found [here]("https://help.ubuntu.com/community/UpgradeNotes").  You will have to upgrade from 6.06 to 6.10, and then from 6.10 to 7.04

Also, keep in mind that if you have installed any packages from outside the standard ubuntu repositories, the upgrade may not go as smoothly as you might like!

---

