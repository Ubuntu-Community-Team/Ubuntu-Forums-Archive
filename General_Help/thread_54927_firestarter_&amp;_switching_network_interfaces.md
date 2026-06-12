---
title: "firestarter &amp; switching network interfaces"
date: 2005-08-06
forum: General Help
---

### Post by knathraak on 2005-08-06
My laptop has wireless and wired network interfaces, which I use one at a time. E.g., I use the wired when at my desk, and switch to wireless when on the couch.

When I switch I have to edit firestarter's preferences to tell it which interface to set rules for.

Does anybody have any ideas how to switch it automatically?

The rules are set using the $IF variable which is set in /etc/firestarter/configuration.
Right now it is set to:
IF="eth0"

When I change to wireless it gets changed to read:
IF="eth1"
and firestarter gets restarted.

I had thought about writing some sort of script to change this when I change interfaces, but I'm not sure how to do it or how to trigger the script (I use network-admin to change profiles).

Any help would be appreciated.

---

### Post by ils_systems on 2005-11-07
I also have 2 interfaces on my laptop, eth0 and wlan0.  I wrote a script that runs in the background and checks which interface is currently active and changes firestarter configuration accordingly.  You could probably modify it to create something that works for you.

#!/bin/sh
while true; do
    ifconfig eth0 |grep -q "inet addr"
    if [ $? = 0 ];
      then
      sed -i 's/wlan0/\eth0/' /etc/firestarter/configuration
    else
      sed -i 's/eth0/\wlan0/' /etc/firestarter/configuration
    fi
    iptables -L |grep -q DROP
    if [ $? != 0 ];
      then  firestarter -s > /dev/null
    fi
  fi
  sleep 5

done

---

### Post by frogotronic on 2008-04-28
> **ils_systems said:**
> I also have 2 interfaces on my laptop, eth0 and wlan0.  I wrote a script that runs in the background and checks which interface is currently active and changes firestarter configuration accordingly.  You could probably modify it to create something that works for you.

#!/bin/sh
while true; do
    ifconfig eth0 |grep -q "inet addr"
    if [ $? = 0 ];
      then
      sed -i 's/wlan0/\eth0/' /etc/firestarter/configuration
    else
      sed -i 's/eth0/\wlan0/' /etc/firestarter/configuration
    fi
    iptables -L |grep -q DROP
    if [ $? != 0 ];
      then  firestarter -s > /dev/null
    fi
  fi
  sleep 5

done

Looks good...How would I get this to run at start-up (in the background)?

---

