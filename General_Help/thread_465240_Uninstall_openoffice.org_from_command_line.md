---
title: "Uninstall openoffice.org from command line"
date: 2007-06-05
forum: General Help
---

### Post by stchman on 2007-06-05
Hello all I am writing some scripts and one of the scripts needs to uninstall openoffice.org in either Edgy of Feisty.  I am speaking of the openoffice that comes installed with either Edgy or Feisty.  Will this command work?

sudo aptitude remove openoffice.org

I believe it should.  Let me know what you think.

---

### Post by Hendrixski on 2007-06-05
:-) yes it will

However there's no guarantee that this purges all of the files rather than simply removing the software.  So if you want that extra 10 Kb of space, then add the purge option, like such:
```
sudo apt-get remove --purge application
```

also, if you're doing a bunch of apt-get removes' make sure to run apt-get autoclean and apt-get clean to take out all of the dependencies of all of the programs you just removed.

Enjoy.

---

### Post by stchman on 2007-06-05
> **Hendrixski said:**
> :-) yes it will

However there's no guarantee that this purges all of the files rather than simply removing the software.  So if you want that extra 10 Kb of space, then add the purge option, like such:
```
sudo apt-get remove --purge application
```

also, if you're doing a bunch of apt-get removes' make sure to run apt-get autoclean and apt-get clean to take out all of the dependencies of all of the programs you just removed.

Enjoy.

Thanks for the tips.  Everything I have read is that 'aptitude' will remove all dependencies.  I need to get into the habit of using aptitude over apt-get.

I love your signature.

---

