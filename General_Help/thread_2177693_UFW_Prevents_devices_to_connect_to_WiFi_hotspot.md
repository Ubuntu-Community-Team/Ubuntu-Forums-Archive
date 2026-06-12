---
title: "UFW Prevents devices to connect to WiFi hotspot"
date: 2013-09-29
forum: General Help
---

### Post by fantab on 2013-09-29
I am trying to use my ethernet connected, Ubuntu powered machine as a WiFi Hotspot to connect to my Netbook and Android Phone.
With NetworkManager not yet supporting WPA through 'infrastructure' I am using [**this script**]("http://paste.ubuntu.com/6169547/"), as described **[HERE]("http://www.webupd8.org/2013/06/how-to-set-up-wireless-hotspot-access.html")**.

I have UFW enabled with some basic rules. The said script helps establish connection to my Netbook and Android if and when the **UFW is disabled**.
When **UFW is enabled** my devices are "*trying to obtain IP*" and disconnect. The problem seems to be with IP MASQUERADE, however I am not sure.

I have tried workaround described [**here**]("https://help.ubuntu.com/13.04/serverguide/firewall.html#ip-masquerading") to enable masquerading through UFW. But I made no progress. I also tried the workaround [here]("http://translate.google.com/translate?hl=en&sl=fr&u=http://doc.ubuntu-fr.org/hostapd&prev=/search%3Fq%3Dhttp://doc.ubuntu-fr.org/hostapd%26biw%3D1920%26bih%3D943"); its bit old but I guess UFW rules still apply.

It will be a great help if the forum can confirm that it is indeed the issue related with 'Masquerading' and help me tweak UFW to allow 'Network Sharing'.

Like I mentioned, if UFW is disabled the said script works and I am able to connect my Netbook and Android Phone to the hotspot and share Internet.
Need help resolving this issue...

(I can provide more info if necessary).

Regards...

---

### Post by fantab on 2013-10-01
BUMP...

I don't feel comfortable using Wifi without UFW.
Any ideas?

---

