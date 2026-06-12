---
title: "systemd cycle errors after upgrading system last night"
date: 2016-11-04
forum: General Help
---

### Post by oscar19772 on 2016-11-04
Hi all!

Last night i have upgraded with apt upgrade, installed some nvidia drivers and other stuff.

Now when i boot i see :

systemd[1]: NetworkManager.service: Job NetworkManager.service/start deleted to break ordering cycle starting with network.target/start
systemd[1]: firewalld.service: Job firewalld.service/start deleted to break ordering cycle starting with network.target/start

how i can solve this? i have noticed there is no firewall rules active.

Thanks.

---

