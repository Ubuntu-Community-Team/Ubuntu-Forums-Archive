---
title: "Firewall paralysing internet connection?"
date: 2005-08-30
forum: General Help
---

### Post by Navyblue on 2005-08-30
First of all, I am not sure if the above assumption of mine is correct as I don't find any sense in it.

I have just installed Firestarter in Ubuntu 5.04 through Synaptic. I connect to the internet through wired LAN by D-Link DSL-G604T Wireless ADSL Router.

After it detected several intrusion attempts (connecting my PocketPC through SynCE is one of them), my internet connection would freeze for sometime (15-30 min). And not only for this system, all other systems connecting to the router would experience the same interruption.

Basically, everytime I were to sync my PocketPC to my system, the internet of the whole network would be down for a while. Even I disable the firewall. (btw my PocketPC would not even connect if the firewall is on)

Restarting the router, rebooting the system, shutting off and even uninstalling the firewall does not help. I am not sure which of the (or the combination of) above actions actually resume the connection.

The firewall settings were the default, I did not mess with it.

Its not the first time that I install Firestarter but it is the first time that I experience internet connection interruption like this.

What is happening here? What should I do?

Thanks for reading.

---

### Post by arnieboy on 2005-08-30
[QUOTE=Navyblue]First of all, I am not sure if the above assumption of mine is correct as I don't find any sense in it.

I have just installed Firestarter in Ubuntu 5.04 through Synaptic. I connect to the internet through wired LAN by D-Link DSL-G604T Wireless ADSL Router.

After it detected several intrusion attempts (connecting my PocketPC through SynCE is one of them), my internet connection would freeze for sometime (15-30 min). And not only for this system, all other systems connecting to the router would experience the same interruption.

Basically, everytime I were to sync my PocketPC to my system, the internet of the whole network would be down for a while. Even I disable the firewall. (btw my PocketPC would not even connect if the firewall is on)

Restarting the router, rebooting the system, shutting off and even uninstalling the firewall does not help. I am not sure which of the (or the combination of) above actions actually resume the connection.

The firewall settings were the default, I did not mess with it.

Its not the first time that I install Firestarter but it is the first time that I experience internet connection interruption like this.

What is happening here? What should I do?

Thanks for reading.[/QUOTE]

Its not because of the linux firewall. check your router to make sure its working properly and u have the wireless thing configured properly.

---

### Post by Navyblue on 2005-08-30
Thanks for the reply.

After some more testing, I am able to let the PocketPC connect without the internet shutting down. But I can't control it or see any pattern whether the firewall would get mad, if I were to see some red coloured access in the event log GUI, that's it for the internet.

SynCE alone -> internet ok
Firestarter alone -> internet ok
SynCE + FIrestarter + black coloured event log -> internet ok
SynCE + FIrestarter + red coloured event log -> internet dies

I have never had any slightest hint of such problem prior to this. What sort of router problem do you think it would be?

Also as mentioned, I connect through wired LAN. And when this thing occur, all system in the network, wired and wireless, Linux and WIndows, suffer the same fate.

---

### Post by arnieboy on 2005-08-30
[QUOTE=Navyblue]Thanks for the reply.

After some more testing, I am able to let the PocketPC connect without the internet shutting down. But I can't control it or see any pattern whether the firewall would get mad, if I were to see some red coloured access in the event log GUI, that's it for the internet.

SynCE alone -> internet ok
Firestarter alone -> internet ok
SynCE + FIrestarter + black coloured event log -> internet ok
SynCE + FIrestarter + red coloured event log -> internet dies

I have never had any slightest hint of such problem prior to this. What sort of router problem do you think it would be?

Also as mentioned, I connect through wired LAN. And when this thing occur, all system in the network, wired and wireless, Linux and WIndows, suffer the same fate.[/QUOTE]

For all problems related to your specific router u should head to this forum:
[http://www.expansys.com/forum.asp?code=110551](http://www.expansys.com/forum.asp?code=110551)

---

