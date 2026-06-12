---
title: "How to configure multiple IP addresses for a single hostname?"
date: 2018-02-28
forum: General Help
---

### Post by yoshioy on 2018-02-28
[COLOR=#333333][FONT=Lato]Question been asked couple years ago, but wondering if there is a solution now. Is there any way to configure multiple static IP address mappings for a single hostname?  (for example, a server with two ethernet ports that each get a distinct IP address). I want to be sending specific data over the two IP addresses to increase bandwidth.

[/FONT][/COLOR][COLOR=#333333][FONT=Lato]Is there a way to assign two IP addresses to the same hostname?[/FONT][/COLOR]

---

### Post by HermanAB on 2018-03-01
This is not a problem. You *can* assign multiple IP addresses to an ethernet port.

For example:
[https://www.ostechnix.com/how-to-assign-multiple-ip-addresses-to-single-network-card-in-linux/](https://www.ostechnix.com/how-to-assign-multiple-ip-addresses-to-single-network-card-in-linux/)
[http://xmodulo.com/how-to-assign-multiple-ip-addresses-to-one-network-interface-on-centos.html](http://xmodulo.com/how-to-assign-multiple-ip-addresses-to-one-network-interface-on-centos.html)

---

### Post by SeijiSensei on 2018-03-01
You won't get any bandwidth improvements that way, though.  For that, you need to use "[bonding]("https://help.ubuntu.com/community/UbuntuBonding")."

---

