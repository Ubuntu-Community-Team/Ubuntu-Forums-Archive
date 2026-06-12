---
title: "Remote Desktop solutions for Xubunto"
date: 2020-01-11
forum: General Help
---

### Post by martyyyn on 2020-01-11
Hello
I can’t find a reliable or simple solution to Remote Desktop into Xubunto from Windows.

Any suggestions would be a appreciated

Thank you

---

### Post by TheFu on 2020-01-11
I've been using x2go for about 5 yrs.  It works over ssh, which is part of the NX protocol.  I've outlined the installation in these forums a few times the last 5 yrs.  Everyone who switched from either VNC or RDP tools to x2go say it is like night and day related to performance.  Plus, if you need access over the internet, because ssh is part of the protocol, just the ssh port needs to be opened and ssh-keys should be used for authentications.  I've used x2go from 5 continents.

---

### Post by martyyyn on 2020-01-11
Thanks! Good advice. It was fairly easy to set up.

---

### Post by ajgreeny on 2020-01-11
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

### Post by TheFu on 2020-01-11
> **martyyyn said:**
> Thanks! Good advice. It was fairly easy to set up.

If performance isn't great, set the image compression to 4K-png and bandwidth to ISDN.  This will make it scream for productivity apps.  Image editors won't like any remote desktop options.

May want to have 2 configurations for access to the system.  One for on the LAN and one for over the internet.

---

