---
title: "Cool stuff to do with bluetooth cellphones?"
date: 2005-10-14
forum: General Help
---

### Post by AndersAA on 2005-10-14
Anyone found anything cool to do with them?

Like auto locking the screen when you leave the computer ( [http://gentoo-wiki.com/TIP_Bluetooth_Proximity_Monitor](http://gentoo-wiki.com/TIP_Bluetooth_Proximity_Monitor) ).

Or maybe using your computer as a remote control (what I'm currently working on).  It was actually pretty simple (use hcitool scan, then when you have the id use hidd --connect <id>), but I'm working on making it better.

Stumbled over [http://gbtcr.chileforge.cl/](http://gbtcr.chileforge.cl/), anyone tested it?  Looks kinda interesting, but had too many dependencies for me to bother tonight.

Also, does anyone know how to setup my computer as the bluetooth server for not only file sharing (with OPUSH) but as hidd.  I want my phone to access the computer and work as a mouse, I dont want to walk over to the computer to use my remote control ;)

---

### Post by systematic on 2006-01-06
> Also, does anyone know how to setup my computer as the bluetooth server for not only file sharing (with OPUSH) but as hidd. I want my phone to access the computer and work as a mouse, I dont want to walk over to the computer to use my remote control

I am running Ubuntu Hoary + bluez-utils... I enabled hid by editing /etc/default/bluez-utils and uncommenting
```
HIDD_ENABLED=1
HIDD_OPTIONS="--master --server"
```

then /etc/init.d/restart/bluez-utils
then on phone remove the bluetooth pairing for the PC and then re-add and search for services.

I was then able to use remote control applications on my sony ericsson v600i to control PC applications...

There is more detail on my website at [http://systematic-ni.co.uk/sitemgr-site/index.php?page_name=products&domain=systematic-ni.co.uk&wikipage=SonyEricsson](http://systematic-ni.co.uk/sitemgr-site/index.php?page_name=products&domain=systematic-ni.co.uk&wikipage=SonyEricsson) on how to create a remote controller for a sony ericsson phone to allow your phone to operate as a remote controller for an OpenOffice presentation....

Now what else can we do?

---

