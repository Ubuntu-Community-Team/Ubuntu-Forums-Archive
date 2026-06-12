---
title: "Sources List for Beryl Emerald"
date: 2008-06-09
forum: General Help
---

### Post by Epidemic_HardyBoy on 2008-06-09
Hi, I'm a horrible newb at Ubuntu.

I need help here. It's probably been solved already, but I can't find it.

When they tell me to "add" sources to my Sources.list file, How do I add them?

```

you need to edit /etc/apt/sources.list file

sudo vi /etc/apt/sources.list

Add the following line for the latest beryl (Both i386&64 bit)

deb http://ubuntu.beryl-project.org feisty main

Save file and exit

Copy the key file using the following command

wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- sudo apt-key add -

Now you need to update the source list using the following command

sudo apt-get update
```

Thanks in advance.

---

### Post by steveneddy on 2008-06-09
What version of Ubuntu are you using?

---

### Post by Epidemic_HardyBoy on 2008-06-09
Ubuntu Hardy Heron 8.04

---

### Post by chewearn on 2008-06-09
Don't use beryl, it's deprecated.  by default, Hardy comes with compiz.  First you enable 3D video graphics driver.  Compiz (with minimal features) will be automatically enabled after that.  For more compiz features, you install CCSM.

---

### Post by Epidemic_HardyBoy on 2008-06-09
If I may ask, what is CCSM?

---

### Post by chewearn on 2008-06-09
> **Epidemic_HardyBoy said:**
> If I may ask, what is CCSM?

Compiz Config Settings Manager.  To install it run this command:
```
sudo apt-get install compizconfig-settings-manager
```

This will give you a new icon to play with, under
System > Preferences > Advanced Desktop Effects Settings

.

---

### Post by Epidemic_HardyBoy on 2008-06-09
:\

Ehh. Wasnt really looking for that type of stuff, but thanks man!

Oh nvm, i see how you do it.

THANKS ALOT MAN!

---

### Post by Forlong on 2008-06-09
Just in case you haven't found out already, here's how to install emerald on Hardy:
```
sudo apt-get install emerald
```
Easy as pie. :)

---

