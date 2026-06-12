---
title: "what do i have to do to totally purge LAMP?"
date: 2006-07-22
forum: General Help
---

### Post by lapsey on 2006-07-22
I have somehow messed up MySQL and Apache to an extent where it would be better to start from fresh.

But no matter what I use to purge -all the items- listed on [https://help.ubuntu.com/community/Drupal](https://help.ubuntu.com/community/Drupal) , the MySQL database and user database - basically everything to do with MySQL persists, even when removed.

How do I rid myself of all this and start from fresh?

---

### Post by Sef on 2006-07-22
How did you install LAMP?

Synaptic, apt-get, aptitude, or other?

---

### Post by SuperMike on 2006-07-22
# apt-get --purge remove php*
# apt-get --purge remove apache*
# apt-get --purge remove mysql*

BE CAREFUL, HOWEVER!!! If you do this and it wants to remove more than just PHP stuff, Apache stuff, or MySQL stuff, such as "ubuntu-desktop", you could be in for a world of frustration. When that occurs, then write down the modules you see on the screen by hand and invididual remove them one by one with:

# apt-get --purge remove <module name>

and ensure it's only going to remove stuff related to PHP, Apache, or MySQL.

Then, to reinstall these, use Synaptic, choose PHP4 or PHP5, pick out individual PHP modules you want, pick your MySQL, pick your MySQL admin tool of preference, and then tell it to install. Synaptic will install everything else for you automatically.

---

### Post by lapsey on 2006-07-23
Thanks guys. It seems that on Debian and Ubuntu certain Apache, MyPHP config files are NOT purged, whether purged via SPM or Aptitude. This includes any MySQL databases, for which I had to learn some basic SQL (boo hoo) to remove.

So in this case it was quicker to fix the installation than to remove and reinstall it. Not that it should be the case.

---

