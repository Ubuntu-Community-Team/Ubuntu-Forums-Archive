---
title: "[SOLVED] Removing applications leaves traces behind"
date: 2008-06-11
forum: General Help
---

### Post by f37u5g0d on 2008-06-11
If I add any program with add/remove or with synaptic and the remove it by either means it leaves files behind.  Specifically if I choose to view hidden files and then look in my home folder I can see .* related to applications I have added and removed already.  This happens even if I choose "complete removal" in synaptic.

Why does ubuntu leave these folders behind?

Is this the only folder that has application traces left over?

I know that when an app is installed it goes into many more folders than "home."  I am concerned because after a long time these traces can really clutter the hard drive and possibly slow down the machine.

Is there a simple way to remove them?

---

### Post by sdennie on 2008-06-11
I don't think it's possible to automatically have things in your home directory removed because they aren't part of the package installation but instead created by the app the first time you run it.  Leaving the dotfiles in your home directory should have no performance implications but, if they bother you, you are welcome to manually remove them.

---

### Post by forestpixie on 2008-06-11
I generally clean them all out when I do a reinstall, just leaving behind those .app folders I will want in the clean install.

---

### Post by brayla on 2008-06-11
MONEY ONLINE JUST TRY AND SEE [http://www.paid-ads.info/?r=brayla](http://www.paid-ads.info/?r=brayla)

---

### Post by f37u5g0d on 2008-06-12
Ok.  Thank you for clearing that up.  I was always confused because I didn't know exactly what folders a given package or application would install too but now I can rest assured that the only files left behind after removal will be in the home folder and any that I have created.

Unfortunately for me the linux filesystem is still a little bit mysterious and unknown.

---

### Post by unutbu on 2008-06-12
If you install package XYZ with

```
sudo apt-get install XYZ
```

and then remove it with

```
sudo apt-get purge XYZ
```

The XYZ deb will still remain in /var/cache/apt/archives.

You can remove it manually with
```

sudo rm /var/cache/apt/archive/XYZ-<something>-.deb
```

or you can clear your entire cache with
```
sudo apt-get clean
```

---

