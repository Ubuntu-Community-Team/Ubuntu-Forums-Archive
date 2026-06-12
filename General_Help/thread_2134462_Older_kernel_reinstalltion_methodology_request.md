---
title: "Older kernel reinstalltion methodology request"
date: 2013-04-11
forum: General Help
---

### Post by kafkaian on 2013-04-11
Am suffering from the Sandybridge regression bug [(click here)]("https://bugs.launchpad.net/ubuntu/precise/+source/linux/+bug/1140716") leading to inoperable GUI as Unity/Gnome classic freeze etc: 

So don't know how long the critical status will last (3.2.0-39), so in checking grub loader I notice I don't appear to have the previous working version available (3.2.0-38 on Precise 12.04 LTS).

Just wondering if someone could advise the best way to get this back. 
Thanks for any help

---

### Post by ibjsb4 on 2013-04-11
Got synaptic?

```
sudo apt-get install synaptic
```

And choose whatever kernel you want :)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9)

---

### Post by kafkaian on 2013-04-11
Thanks ibj, but I think CLI is the only route I can take on the affected machine.

I know how to sudo apt-get install linux-source-3.2.0.38 kernel-package libncurses5-dev fakeroot etc, but I'm more concerned about getting any dependencies right and whether I need to pull back on other updates accordingly.

---

