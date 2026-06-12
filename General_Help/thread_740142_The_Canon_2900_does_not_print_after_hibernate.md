---
title: "The Canon 2900 does not print after hibernate"
date: 2008-03-30
forum: General Help
---

### Post by RussianMan on 2008-03-30
All greetings! 
I have printer Canon 2900 adjusted on [this](http://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900) How-To.
It ceases to work after an output from hiberante.
I am am helped by a command: sudo/etc/init.d/ccpd restart
How to make that it it was carried out automatically after hiberante a computer?

At me Ubuntu 7.10 At a Russian-speaking forum to me anything could not advise. 
And I badly write in English :-(

---

### Post by warp99 on 2008-03-30
You need to add the ccpd comand to your acpi-support file. Do the following:

```
sudo gedit /etc/default/acpi-support
```

scroll down until you see the following:

```
# Add services to this list to stop them before suspend and restart them in
# the resume process.
STOP_SERVICES=""

```

add your service:

```
# Add services to this list to stop them before suspend and restart them in
# the resume process.
STOP_SERVICES="ccpd"

```

Save the file and your done. If you have more than one service to stop put a space between each service.

---

### Post by RussianMan on 2008-04-07
Ubuntu is excellent!

---

