---
title: "Window User Looking To Install Ubuntu Server?"
date: 2007-05-22
forum: General Help
---

### Post by klgsx on 2007-05-22
Been playing around with Ubuntu for a while not.  So far no problems with the Ubuntu desktop in my laptop. Life is good...BUT... now i like to get my hands dirty with Ubuntu Server.

Got an old dell HP machine with 20GB Hard Drive and 2 GB of ram.   I love to install Ubuntu Server, but so far i have notice that the Ubuntu Server does not have a GUI... Everything done tru command line :-(

So here are is my question. 

After downloading and successfully installing the Ubuntu Server can I Install some kind of GUI to run some basics admin actions such as add users, create share folders for users, configure network adapter, etc?

Any suggestions is more than welcome.

Thanks.

---

### Post by blind0wl on 2007-05-22
Take a look at this website [http://www.ubuntugeek.com/ubuntu-704-feisty-fawn-lamp-server-setup.html]("http://www.ubuntugeek.com/ubuntu-704-feisty-fawn-lamp-server-setup.html")

Will give you all the instructions, with screenshots.  Yes you can add a gui, just apt-get install ubuntu-desktop.

The guide above also tells you how to do so.

Cheers

Blindy

---

### Post by zvacet on 2007-05-23
If you want GNOME

```
sudo aptitude install ubuntu-desktop
```

and if you prefer KDE

```
sudo aptitude install kubuntu-desktop
```

---

