---
title: "Can't seem to get a connection with Ethernet"
date: 2012-12-03
forum: General Help
---

### Post by Rocket J Squirrel on 2012-12-03
Hmmm. I've bee working on some LAN issues here in our small office. I've wanted to use this little laptop to ping at and dink with hosts on the LAN, but when I shut off Wireless (wlan0) and connect an Ethernet cable to the port, I get nothing. There's no indication that the laptop is using the wired connection.

What are the steps I should take to troubleshoot this issue?

---

### Post by mamamia88 on 2012-12-03
try ```
sudo dhclient eth0

```

---

### Post by Rocket J Squirrel on 2012-12-04
Thank you, mamamia88

Should the wireless be turned off before doing this?

---

