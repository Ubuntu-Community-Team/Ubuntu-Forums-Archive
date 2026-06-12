---
title: "Port is allowed by UFW but still is closed. Connection is denied by Qbittorrent"
date: 2013-12-13
forum: General Help
---

### Post by deaton25 on 2013-12-13
my incoming port is allowed by ufw but remains closed and connection is denied by ubuntu qbittorrent, Why? ps: i have open DNS

---

### Post by bashiergui on 2013-12-13
We can't tell you without more details. You need to determine if it's not going through because of your ufw firewall or if it's your ISP blocking the port. Test it by turning the ufw firewall off completely and see if it goes through. Read the ufw logs to determine if there's a port being used that ufw is blocking.

See this for some pointers. [http://www.techsupportalert.com/optimizing-qbittorrent-speed](http://www.techsupportalert.com/optimizing-qbittorrent-speed)

---

### Post by tomearp on 2013-12-13
It sounds like you may need to forward the incoming port in your router's settings.
I'm not familiar with qbittorrent but there may be an option to use UPnP to automatically tell the router to forward the port, assuming your router supports UPnP.

---

