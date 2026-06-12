---
title: "Lubuntu 13.10, Startup programs won't load when start up."
date: 2014-02-24
forum: General Help
---

### Post by hirotop on 2014-02-24
Hi, 

Recently, I upgraded from lubuntu 13.04 to lubuntu 13.10. During the upgrade, it says there was errors and it restores back to 13.04. 

However, after rebooting, the system looks different and the information says that it is lubuntu 13.10. 

I am fine with that but, I realize that there are several features missing in my computer. 

1) startup programs won't start automatically. 
 -> I have to start them to use them. For example, dropbox won't start by itself. It is registered as startup program, of course. 

2) after 'sleep', it doesn't ask me to enter the passwd of my session. 

Does anyone have any idea on these?

Thanks.

---

### Post by Dennis N on 2014-02-24
In Lubuntu 13.10, place commands for startup programs in:

~/.config/lxsession/lubuntu/autostart

These would autostart upon logging in.

---

### Post by hirotop on 2014-02-24
Thank you so much! It works well. But I still don't understand why the original system does not work.

---

