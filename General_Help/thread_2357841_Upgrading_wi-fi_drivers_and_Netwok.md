---
title: "Upgrading wi-fi drivers and Netwok"
date: 2017-04-06
forum: General Help
---

### Post by anon_private on 2017-04-06
My current version of kubuntu connects to the router via wi-fi without a problem.

Recently, I created a LiveDVD for version 16 (both kubuntu and ubuntu  (gnome)), I noticed that the wi-fi connection repeatedly drops.

It occurs to me that my drivers and networking software may not be up to date.

Can I check the wi-fi drivers and networking software? It would be  important to ensure a roll-back procedure in case the latest softwares  caused a problem with my current, and, working, edition of kubuntu.

Thanks

---

### Post by kc1di on 2017-04-08
Hello anon_private,
First lets get a look at your total machine.
please got to a terminal and install inxi like this ```
sudo apt-get install inxi
```
once that is install type in the terminal ```
inxi -Fxz
``` and copy and past the output here. 
That should give us the info need to help.

---

