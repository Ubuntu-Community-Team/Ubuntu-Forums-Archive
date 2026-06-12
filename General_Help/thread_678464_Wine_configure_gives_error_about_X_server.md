---
title: "Wine configure gives error about X server"
date: 2008-01-25
forum: General Help
---

### Post by AlP36 on 2008-01-25
using: Ubuntu 6.06 LTS
I down loaded wine from the Ubuntu repository yesterday. When I tried to configure with "winecfg" in terminal I get the following message. 
wine: creating configuration directory '/root/.wine'...
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

Could some one give me some direction on this?

---

### Post by taurus on 2008-01-25
First of, you are running a desktop version, not the server, right?

However, why did you run **winecfg** as root?  Should run it with your regular account to configure it.

---

### Post by AlP36 on 2008-01-25
I am running desktop. I will try config in my regular account. 

Thanks

---

### Post by AlP36 on 2008-01-25
Ok That solved my pronblem. I suppose I thought to configure things I would need to be in root.

Thanks again.

---

