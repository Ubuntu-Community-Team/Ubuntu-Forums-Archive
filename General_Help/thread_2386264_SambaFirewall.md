---
title: "Samba/Firewall"
date: 2018-03-03
forum: General Help
---

### Post by don43 on 2018-03-03
I have setup share on Ubuntu, when trying from Windows to see them it would not connect. The Windows troubleshooting indicated it was possibly the Ubuntu firewall blocking the share.

From what I could find adding these ports to the ufw works

[COLOR=#000000]*sudo ufw allow proto udp from 192.168.1.0/24 to any port 137*[/COLOR]
[COLOR=#000000]*sudo ufw allow proto udp from 192.168.1.0/24 to any port 138*[/COLOR]
[COLOR=#000000]*sudo ufw allow proto tcp from 192.168.1.0/24 to any port 139*[/COLOR]
[COLOR=#000000][I]sudo ufw allow proto tcp from 192.168.1.0/24 to any port 445

Or just:

[/I][/COLOR]sudo ufw allow Samba

[COLOR=#000000]*Are either OK, one better than the other?*[/COLOR]

[COLOR=#000000]*I have Comcast so my IP starts with 10 instead of 192.*[/COLOR]

---

### Post by ubname on 2018-03-03
Have you enabled the ubuntu firewall? I do not think it's enabled by default so the problem may be something else,
*if* the problem is the firewall sudo ufw allow Samba should do.

---

