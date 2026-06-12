---
title: "SUMO Help needed"
date: 2015-10-16
forum: General Help
---

### Post by mh-mithun on 2015-10-16
I downloaded Sumo 0.22.0. I did ./configure then make but when I do sudo make install it says 
```

make[1]: Entering directory '/home/hasan/sumo/application/sumo-0.22.0/bin'
make[1]: Nothing to be done for 'install'.
make[1]: Leaving directory '/home/hasan/sumo/application/sumo-0.22.0/bin'
make[1]: Entering directory '/home/hasan/sumo/application/sumo-0.22.0'
make[2]: Entering directory '/home/hasan/sumo/application/sumo-0.22.0'
make[2]: Nothing to be done for 'install-exec-am'.
make[2]: Nothing to be done for 'install-data-am'.
make[2]: Leaving directory '/home/hasan/sumo/application/sumo-0.22.0'
make[1]: Leaving directory '/home/hasan/sumo/application/sumo-0.22.0'
root@lucid:/home/hasan/sumo/application/sumo-0.22.0# sumo-gui
The program 'sumo-gui' is currently not installed. You can install it by typing:
apt-get install sumo



```
I tried sumo --help it gives some info like :
```

GUI Only Options:
  --gui-settings-file FILE             Load visualisation settings from FILE
  -Q, --quit-on-end                    Quits the GUI when the simulation stops
  -G, --game                           Start the GUI in gaming mode
  -S, --start                          Start the simulation after loading
  -T, --disable-textures               Do not load background pictures




Examples:
  sumo -b 0 -e 1000 -n net.xml -r routes.xml
    start a simulation from time 0 to 1000 with given net and routes
  sumo -c munich_config.cfg
    start with a configuration file
  sumo --help
    print help



```
Which means the application is there .so my question is why it it is not giving the gui version

---

### Post by Bucky Ball on 2015-10-16
*Thread moved to **General Help**.*

Installations and Upgrades area concerns the OS itself. Good luck. :)

---

### Post by coffeecat on 2015-10-16
This bit from the terminal output:

> **mh-mithun said:**
> ```

The program 'sumo-gui' is currently not installed. You can install it by typing:
apt-get install sumo

```

I have no idea why the downloaded source code doesn't include the GUI, but the open source licence will probably mean that you can get the source code for sumo-gui somewhere on their website. If you sudo apt-get install sumo, you'll get an older version of sumo than the one you are trying to install - currently 0.21 in Ubuntu 15.04 compared with the 0.22 you are trying to install.

Why are you doing it the hard way? Either install the slightly earlier 0.21 version using Software Centre or apt-get (or Synaptic if you use it), or enable this PPA repository and install the 0.24 version:

[https://launchpad.net/~sumo/+archive/ubuntu/stable](https://launchpad.net/~sumo/+archive/ubuntu/stable)

---

