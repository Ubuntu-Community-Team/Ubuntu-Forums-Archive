---
title: "ip configuration and routes not being saved, they change after reboot"
date: 2020-02-21
forum: General Help
---

### Post by felipe-bravo-silva on 2020-02-21
I installed lubuntu on my old laptop, which has 2 ethernet ports, ideal for my little project that uses 2 isolated networks.
The problem is, one of the ethernet ports doesn't save its settings, which is a fixed IP and a route .
No matter if I configure it using the cockpit or the UI, still not touching the config files since I rather let the OS do it, but will do if necesary.
How can I check if the configuration is being saved before rebooting?

Both ports work fine, the only problem is the IP and route configuration on the 2nd port not being saved after reboot.

---

### Post by felipe-bravo-silva on 2020-02-21
had to manually delete the OS-created interfaces, then create them myself, that solved the problem

---

