---
title: "simple-scan firewall rules for WIFI - Gufw"
date: 2015-09-30
forum: General Help
---

### Post by nknwn on 2015-09-30
Hi all, I have a Wireless Epson printer SX-235. I can print OK, but Scan is blocked by the Firewall - If I turn off the Firewall then Scan is OK.
So the question is: What should I enter in Gufw to make a rule to unblock simple-scan?
[ATTACH=CONFIG]264760[/ATTACH][ATTACH=CONFIG]264759[/ATTACH]

Thanks for any help in advance

---

### Post by nknwn on 2015-10-01
Have fixed it with the following command in the terminal:
[B]sudo ufw allow from 192.168.1.5

[/B]How-to UFW here: [http://ubuntuforums.org/showthread.php?t=823741](http://ubuntuforums.org/showthread.php?t=823741)
The IP address for the printer was available to check in the router's control panel. It might change in future (if I power down) and I'll keep an eye out for that

The above command added a new rule for the firewall.
However I was unable to check what it looked like in Gufw. I found I could not see the details as Gufw is not allowed to edit this rule.
That doesn't matter now as I won't be using Gufw in future for creating rules.

---

