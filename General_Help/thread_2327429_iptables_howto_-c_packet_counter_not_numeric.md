---
title: "iptables howto -c packet counter not numeric"
date: 2016-06-10
forum: General Help
---

### Post by greg112 on 2016-06-10
I have recently installed Ubuntu 16.04 on my VPS and am trying to get iptables set up, but following the [https://help.ubuntu.com/community/IptablesHowTo#Allowing_Established_Sessions](https://help.ubuntu.com/community/IptablesHowTo#Allowing_Established_Sessions), when I enter ```
iptables -A INPUT -m conntrack -ctstate ESTABLISHED,RELATED -j ACCEPT
``` I get the following error: ```
iptables v1.6.0: -c packet counter not numeric
```
I've tried ```
iptables -Z
```
but that's not working... Just below that I saw > [COLOR=#333333][FONT=Ubuntu]If the line above doesn't work, you may be on a castrated VPS whose provider has not made available the extension...[/FONT][/COLOR] so do I need to install an extension for conntrack?

TIA

---

### Post by greg112 on 2016-06-10
Never mind, apparently adding a rule with ```
... -m state -state ...
``` initiated the counter. After a ```
iptables -F
``` it works as stated.

So the question now becomes: is there something I missed that would initialize the counter without having to do the above?

TIA

---

