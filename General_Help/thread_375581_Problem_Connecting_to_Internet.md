---
title: "Problem Connecting to Internet"
date: 2007-03-03
forum: General Help
---

### Post by hemple on 2007-03-03
I was using  my internet without any problems. Then I went out of the country for ten days and I just got back today. And I am not able to connect to internet. The network is open without a password so some buddies who are over a lot can access the network easily on their laptops. My friend can see my network and is able to get on the internet. Why am I having troubles and how can I fix it? Thanks

---

### Post by tgalati4 on 2007-03-03
Sounds like your IP lease expired.

Try in a terminal:

sudo ifconfig eth0 down
sudo ifconfig eth0 up

---

