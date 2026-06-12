---
title: "i new to ubuntu need help"
date: 2008-03-03
forum: General Help
---

### Post by jcatvbuk on 2008-03-03
i m new to ubuntu and live in san antonio texas and installed ubuntu 7.1 on mycompac presario laptop yesterday and now i need drivers for everything from broadcom43xx wireless card to youtube. not usre where to even start

---

### Post by iSplicer on 2008-03-03
Hello and welcome to Ubuntu!

Have you completely updata your System? Go to the terminal and type in:

```
sudo apt-get update
```

And as for youtube, you should see firefox automatically attempt to install adobe flash player

Good Luck!

---

### Post by tad1073 on 2008-03-03
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

system menu>Administration>Synaptic Package Manager-do a search for flash player non-free

---

### Post by jcwmoore on 2008-03-03
what sort of drivers are you missing? what hardware? as for the you tube thing, you need to install the non free flash plug in, go to 
System > Admin > Synaptic Package Manager

once there go to 
Settings> Repositories

Make sure you have every thing selected, close the window, and click Reload,

Then do a search for Flash Plugin nonfree and you should find the package you need to install

---

