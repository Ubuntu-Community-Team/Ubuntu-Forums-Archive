---
title: "Can't Update Install"
date: 2007-11-15
forum: General Help
---

### Post by jjb123 on 2007-11-15
Hi, I can't seem to update anything on my Kubuntu 7.10 install. Whenever adept says there is updates I click on the icon, enter my password, fetch updates, and click install and when it gets to the end each time it say "Can not commit changes." and the update fails. What's wrong? Thanks. :)

---

### Post by solar george on 2007-11-15
Open a command line and type 

```
sudo apt-get full-upgrade
```

If it fails post the output.

---

### Post by ericatman on 2007-11-15
> **solar george said:**
> Open a command line and type 

```
sudo apt-get full-upgrade
```

If it fails post the output.

i have the same problem and when i tried your command i got an error
E: Invalid operation full-upgrade

thanks in advance

---

### Post by jjb123 on 2007-11-15
Ok, I tried that and it said that full-upgrade was an invalid operation.

---

### Post by solar george on 2007-11-15
Try apt-get dist-upgrade instead.

---

### Post by lemming552 on 2007-11-17
Post #2 in [This thread](http://ubuntuforums.org/showthread.php?t=420759) solved it for me.

> **falm said:**
> Hello,
i had the same problem, after

sudo rm /var/lib/dpkg/lock
sudo rm /var/cache/apt/archives/lock
sudo dpkg --configure -a
  -> read the output, you will have to answer a few questions
sudo dpkg --configure --pending

everything is working again

---

