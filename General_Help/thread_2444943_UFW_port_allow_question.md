---
title: "UFW port allow question"
date: 2020-06-06
forum: General Help
---

### Post by T6&amp;sfpER35% on 2020-06-06
Hi

I want to set a rule in UFW to allow incoming traffic only for qBitTorrent.
I don't want to use the port option cause my VPN uses same port as i set in qBitTorrent, i want to use the <services> option.```
[COLOR=#333333][FONT=UbuntuMono]sudo ufw allow <service name>[/FONT][/COLOR]
```
When i run ```
[COLOR=#333333][FONT=UbuntuMono]less /etc/services[/FONT][/COLOR]
``` , i don't see qBitTorrent anywhere as a service.
In a previous distro i had UFW as a GUI and there i could just type in qBitTorrent under rules,but now in xUbuntu 20.04 i cant find a GUI for firewall.

Any idea how i could set this up?

Thanks.

---

### Post by rattskjelke on 2020-06-06
Xubuntu doesn't have a firewall GUI installed by default.
Most people probably use [gufw]("http://gufw.org").
It's in the standard repos and called Firewall Configuration in the software center and menu.
I don't use qBitTorrent but I just checked and it appears to be one of the predefined gufw rules.

---

### Post by T6&amp;sfpER35% on 2020-06-07
Thanks!
It's what i had before.Works perfect.

---

