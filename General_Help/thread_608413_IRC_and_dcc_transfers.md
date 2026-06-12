---
title: "IRC and dcc transfers"
date: 2007-11-10
forum: General Help
---

### Post by phatbastard on 2007-11-10
Alright, i configured shorewall and my router is taken care of, but i cannot figure out how to get xchat not to fail on dcc transfers. I know shorewall if blocking my incoming dcc transfers and there is just too many ports that dcc uses. Shutting of shorewall and my dcc transfers work. So i modprobed for ip_conntrack_irc and did a 'sudo modprobe ip_conntrack_irc' and that still doesnt work any ideas? Its been a few years since i installed shorewall and had same problem, in my previous attempt to fix this some years ago 'modprobe ip_conntrack_irc' worked

---

### Post by tubasoldier on 2007-11-10
check the Xchat config and make shure it is binding to the correct ip address. That has always been my problem.

---

### Post by ruibernardo on 2007-11-10
Do you have the file "module" in /etc/shorewall? You may need to load the iptables modules for irc. In that file add:
```
loadmodule ip_conntrack_irc
loadmodule ip_nat_irc

```Then restart shorewall with
```
sudo shorewall restart
```An example of the module file in shorewall can be found in /usr/share/doc/shorewall/default-config/modules.

---

