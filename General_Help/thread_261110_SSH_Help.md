---
title: "SSH Help"
date: 2006-09-19
forum: General Help
---

### Post by Adrayic on 2006-09-19
I'm running a clean install of Ubuntu 6.06 LTS. I installed SSH and verified that the daemon was running. I can connect to my box via PUTTY on all local computers in my network but for the life of me I can't connect to it outside the network. Port 22 is open on my router and I havn't touched the configuration files (ssh_config and sshd_config). I have contacted my ISP and they assured me that they wern't blocking any ports. I also tried connecting my computer directly into the modem (bypassing the router) -- same problem. I'm lost... I'm a linux newb and this is really starting to frustrate me!! Any help you could provide would be greatly appreciated. Thanks

---

### Post by PriceChild on 2006-09-19
Not only should you have port 22 open, but you need it forwarded to your specific computer.

---

### Post by Adrayic on 2006-09-19
I have it forwarded to the Ubuntu box IP -- I have triple checked this :)

---

### Post by marianom on 2006-09-19
I assume you can ping your static/dynamic IP from outside. Is it right?
What's the error message you get with putty when you try to connect?

---

