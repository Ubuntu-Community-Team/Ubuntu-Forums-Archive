---
title: "When server booting without keyboard and monitor"
date: 2015-03-04
forum: General Help
---

### Post by hillboy2 on 2015-03-04
I have a small web server that will be doing some data logging (serial ports), processing, relay and html data display on a local network installed on my sailboat. While testing at home I have a keyboard and monitor hooked up but all my work is being done over SSH terminal and SFTP on my main computer. On the boat I'll have a laptop to work on the server unit. I have the motherboard set to power on automatically and so the server is just subject to sudden power off and power on. 

At power on I occasionally see that the attached monitor asks if I really want to boot Xubuntu or run a memory check (and some other option). If this happens in my live environment where there will not be a monitor or keyboard attached what is going to happen?

---

### Post by nerdtron on 2015-03-04
> At power on I occasionally see that the attached monitor asks if I  really want to boot Xubuntu or run a memory check (and some other  option). If this happens in my live environment where there will not be a  monitor or keyboard attached what is going to happen?

There should be a counter on the bottom. I think 10 secs, and it will boot the currently selected option.

---

