---
title: "[SOLVED] So now I'm regretting Automatix...what to do?"
date: 2007-10-05
forum: General Help
---

### Post by zachthejones on 2007-10-05
Okay, I've gathered from some forum reading and a little technical reading that I made a less than intelligent choice installing Automatix when I first setup Ubuntu. I want to get rid of it (and the dangers therein) and at the same time still be able to use a few of the programs I discovered through it.

1) Should I uninstall all the programs I installed through Automatix and then reinstall them manually ("sudo apt-get"-style)? If so, should I uninstall them through Automatix's uninstall function, or do it manually?

2) What's the best way to remove Automatix? "sudo apt-get remove automatix"?

3) The main program I use that I got through Automatix is gDesklets (But I'm not 100% sure I installed it through Automatix, though it shows up in Automatix's uninstall section). And really the only function of it I use is it's StarterBar, which is pretty similar to Apple's application launching bar.  I've heard of Screenlets, and I'm running Beryl, but I don't know if it's got a similar (or better!) application launching bar.

---

### Post by por100pre1 on 2007-10-05
If the programs are working fine leave them. Backup your sources.list (in case Automatix breaks it, you will have a backup):

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```

Then uninstall Automatix:

```
sudo apt-get remove automatix2
```

---

### Post by zachthejones on 2007-10-06
Thanks a bunch for your help! after backing up the sources list, I used the remove command you gave me. in the removal process it gave me this:```
The following packages were automatically installed and are no longer required:
  libevent-execflow-perl libintl-perl cdda2wav python2.4-minimal python2.4
  libsdl-sound1.2 libevent-rpc-perl ogmtools gtk2-ex-formfactory-perl icedax
  lsdvd anyevent-perl planetpenguin-racer-data libevent-perl
Use 'apt-get autoremove' to remove them.

```

do I need to run "apt-get autoremove"?

---

### Post by bodhi.zazen on 2007-10-09
> **zachthejones said:**
> Thanks a bunch for your help! after backing up the sources list, I used the remove command you gave me. in the removal process it gave me this:```
The following packages were automatically installed and are no longer required:
  libevent-execflow-perl libintl-perl cdda2wav python2.4-minimal python2.4
  libsdl-sound1.2 libevent-rpc-perl ogmtools gtk2-ex-formfactory-perl icedax
  lsdvd anyevent-perl planetpenguin-racer-data libevent-perl
Use 'apt-get autoremove' to remove them.

```

do I need to run "apt-get autoremove"?

No you do not "need" to do that, but the packages on that list are not in use and can be removed if desired.

```
sudo apt-get autoremove
```

---

### Post by zachthejones on 2007-10-14
thanks a bunch! I've removed Automatix2 (seemingly) without any disastrous repercussions, and I autoremoved that extra stuff just for clean-up purposes.

---

