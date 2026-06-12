---
title: "Feisty: Cannot authenticate phpMyAdmin"
date: 2007-04-21
forum: General Help
---

### Post by sabrewulf on 2007-04-21
Nothing to explain, really...  my problem is a carbon copy of this guy's problem:

[http://ubuntuforums.org/showthread.php?t=391683&highlight=phpmyadmin](http://ubuntuforums.org/showthread.php?t=391683&highlight=phpmyadmin)

> I can't get phpmyadmin to authenticate. I keep getting this error when I try to log in as root:
Error
#1045 - Access denied for user 'www-data'@'localhost' (using password: YES)

I think mysql is configured properly. I have no problem logging in as root from the console. I never had any issues with phpmyadmin on Dapper.

I would really appreciate some suggestions.

I thought it was something to do with the upgrade at first but I tried again with a fresh install from the Feisty CD and am still having the same issue.

---

### Post by shadwstalkr on 2007-04-21
I had the same problem, but reinstalling php5 fixed it.  Hope that works for you too.

Use the following command:
```
sudo apt-get --reinstall install php5
```
or select php5 for reinstall in Synaptic.

---

### Post by shadwstalkr on 2007-04-21
I spoke too soon.  That only sort of works.  I have to log in again every couple of pages.

---

### Post by sabrewulf on 2007-04-21
> **shadwstalkr said:**
> I spoke too soon.  That only sort of works.  I have to log in again every couple of pages.

Yeah that's the same thing it was doing for me at first, but then it just stopped working altogether :(

---

### Post by sabrewulf on 2007-04-22
bump, anybody?

---

