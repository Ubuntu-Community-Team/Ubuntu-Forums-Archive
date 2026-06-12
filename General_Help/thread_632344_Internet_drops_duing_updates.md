---
title: "Internet drops duing updates"
date: 2007-12-05
forum: General Help
---

### Post by Raptor45 on 2007-12-05
I was wondering if anyone could help me track this down.

My wireless internet connection seems to fail frequently when checking for and downloading updates. Most other times it is stable. Network manager still says its connected, but there is no traffic. If I cancel the updates quickly sometimes it comes back.

Any ideas?

---

### Post by FakeOutdoorsman on 2007-12-07
Try choosing a new repository server. System -> Administration -> Software Sources -> Ubuntu Software Tab. Choose the dropdown menu and click "Other...". A list of servers will appear sorted by country. Test some to see which is fastest or you can try "Select Best Server" which will ping servers and will attempt to pick the fastest for you. Manually choosing a close mirror server resulted in the best speed for me, especially during new Ubuntu releases.

---

### Post by Raptor45 on 2007-12-08
Its not a speed issue, its a connection issue. My whole network goes out, and then is unable to reconnect for a long time.

The only thing I can find in the logs that seems to happen is it says "wlan0: CTS protection disabled"

---

### Post by FakeOutdoorsman on 2007-12-08
Does resetting your router allow you to reconnect?

---

### Post by Raptor45 on 2007-12-08
The router isn't dropping, its the wireless card in the computer. Restarting fixes it.

---

