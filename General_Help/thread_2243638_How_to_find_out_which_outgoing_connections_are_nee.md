---
title: "How to find out which outgoing connections are needed?"
date: 2014-09-10
forum: General Help
---

### Post by klundermann on 2014-09-10
I'd like to configure the UFW firewall to allow only certain outgoing connections.  Since I'm quite a noob at this kind of thing, I'm wondering whether there is a tool that would allow me to see which ports and protocols my system uses when I attempt various tasks.  For example, let's say I print a file on my wireless printer; is there something I could run that would show the connections my machine makes in submitting the print job?

---

### Post by TheFu on 2014-09-10
netstat and lsof are how I would research this. [https://unix.stackexchange.com/questions/56453/how-can-i-monitor-all-outgoing-requests-connections-from-my-machine](https://unix.stackexchange.com/questions/56453/how-can-i-monitor-all-outgoing-requests-connections-from-my-machine)

Plus looking through /etc/services might help.

BTW - UFW is just an interface into the real firewall, iptables. Only Linux systems there is only 1 firewall, iptables. Everything else is an interface to that tool.

Enjoy the power!

---

