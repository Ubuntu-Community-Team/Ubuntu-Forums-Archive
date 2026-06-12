---
title: "Executing a script when connecting on different network interfaces"
date: 2008-02-16
forum: General Help
---

### Post by markonhismobile on 2008-02-16
I'm wondering if it's possible to setup a script to run depending on what network interface I'm connected with. 

I'm running conky on my laptop and change between using the wired and wireless lan interfaces sometimes and just wanted conky to be able to display connection information from. I already have a couple of scripts setup that can change to the relevant conky config file and restart conky.

I looked into placing the scripts into the /etc/network/if-up.d but don't know how to get them to execute for each interface? Would I just need to create an entry in /etc/network/interfaces for eth0 and eth1 and then point to relevant script?

---

