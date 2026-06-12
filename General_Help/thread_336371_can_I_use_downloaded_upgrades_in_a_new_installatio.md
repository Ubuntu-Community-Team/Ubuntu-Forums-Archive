---
title: "can I use downloaded upgrades in a new installation?"
date: 2007-01-11
forum: General Help
---

### Post by ryu kun on 2007-01-11
I am going to reinstall my Ubuntu Dapper and I know that after installation my new Dapper will want to download many upgrades. 

I was wondering if there is a way to use these upgrades in a future installation? I don't want to download the same stuff again and again, because I have a download limit.

Thanks in advance.

---

### Post by MontanaMax on 2007-01-11
any packages that are downloaded are cached locally until you clean them out with something like

```
sudo apt-get autoclean
```

which in your case might not be a good idea. :)

If you want to save the downloaded packages off to a local hard drive and use them for future installations of Ubuntu, that's possible too with something like the personal repository

[https://help.ubuntu.com/community/Repositories/Personal](https://help.ubuntu.com/community/Repositories/Personal)

---

### Post by cmost on 2007-01-11
You could get everything up-to-date and then roll a new Live-CD...  Just a suggestion.  This site will show you how.  Good luck!

[http://wiki.oss-watch.ac.uk/UbuntuDapper/Remaster](http://wiki.oss-watch.ac.uk/UbuntuDapper/Remaster)

---

### Post by schilcha on 2007-01-11
(On my system) downloaded packages are stored in the directory /var/cache/apt/archives you can save these before re-installing and install them again afterwards with dpkg -i.

You might also try to copy the contents of /var/cache/apt/archives back to that directory on the new system. Maybe these will be used in the update marathon after installation. But, I've never tried this -- just a guess.

Good luck!

---

