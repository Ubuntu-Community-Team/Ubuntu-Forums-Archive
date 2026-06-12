---
title: "Landscape - Servers with 22.04 cannot finish activities"
date: 2023-05-12
forum: General Help
---

### Post by jeroen.vanderlinde on 2023-05-12
We are using Landscape (cloud based) and have around 35 servers  connected to it. Most of them are 18.04, but we are now migrating those  servers to 22.04. So some of them are 22.04 now.


 All servers report to Landscape as supposed to (package updates,  reboots, etc). But when Landscape starts an activity based on such a  report, that activity gets stuck on 22.04 servers, but it works just  fine at 18.04 servers.

 
Does anyone has a clue what is happening and point me in the right direction here?

---

### Post by idmbe on 2023-05-13
For me i use landscape with 22.04 "one server" it's work very well and it's activated.

maybe you need to re-check licenses or authentication ... also re-check if landscape client already on 22.04 installed:
```
 sudo apt-get install landscape-client
```


Check this manual, maybe it will be helpful
[https://ubuntu.com/landscape/docs/api-activities](https://ubuntu.com/landscape/docs/api-activities)

---

