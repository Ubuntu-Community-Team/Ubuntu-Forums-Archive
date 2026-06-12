---
title: "Capturing sleep, hibernate and wakeup events"
date: 2021-03-31
forum: General Help
---

### Post by apoorva-ask03 on 2021-03-31
Explored 2 options to capture these power events, but unfortunately none of them worked as expected. 


1. DBus works on desktop but these events also need to be captured on laptops and Linux environments without any GUI. Is there a way to use DBus in both environments?
2. Acpid requires us to write scripts and put these scripts in specific paths and in turn these scripts call the required running application. In the opensource implementation,  the latest version uses netlink sockets to catch the signal. Tried to capture the events using netlink which worked when running on the VM but unfortunately, did not work on Ubuntu 20.04 physical machine/desktop.


Is there any other way to capture these events?

---

