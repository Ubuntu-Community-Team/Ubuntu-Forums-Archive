---
title: "xrdp Configuration"
date: 2019-01-09
forum: General Help
---

### Post by irishjd on 2019-01-09
I have an install of SecurityOnion (16.04.5.5) that is build on Ubuntu 16.04. I installed xrdp and allowed it through the firewall ([COLOR=#333333][FONT=UbuntuMono]sudo ufw allow 3389/tcp). When I try to connect to it via an RDP client, it connects fine but all I see is a blank box (screen-shot 1)
[/FONT][/COLOR][ATTACH=CONFIG]282162[/ATTACH]
If I click on the empty box in the lower right-hand corner, I then see the "X" login prompt but with no text (screen-shot 2)
[ATTACH=CONFIG]282163[/ATTACH]
If I enter a username in the second box and a password in the third box, I get the same windows in screen-shot 1. So it is in a loop. Here is my xrdp config:
[ATTACH=CONFIG]282164[/ATTACH]

Any ideas why this isn't working for me?

Thanks!
Jon

---

### Post by HermanAB on 2019-01-09
Older versions of Ubuntu doesn't use X, so Xrdp won't work.

Someone finally saw the light and dropped support for Wayland, so Xorg is now an option again.

---

