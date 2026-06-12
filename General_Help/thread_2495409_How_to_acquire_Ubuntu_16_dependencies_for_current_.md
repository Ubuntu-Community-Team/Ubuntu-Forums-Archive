---
title: "How to acquire Ubuntu 16 dependencies for current Chromium?"
date: 2024-02-17
forum: General Help
---

### Post by johsal on 2024-02-17
I'm in a standalone version of Ungoogled Chromium so I know it's possible despite how badly developers want us to start from scratch with new os. 



How can I get 120s Chromium .deb for Xenial?

---

### Post by ajgreeny on 2024-02-17
The simple answer is that you can't and shouldn't, and if it were possible it would put you and your OS at great risk as it has had no security upgrades for about 3 years.
It would also put other users on the network at risk so please, please don't do it.

You really should install another fully supported version either 23.10 or the last LTS version, 22.04.
23.10, should you choose that will be upgradable in April to the next LTS version, 24.04.

---

### Post by kostkon on 2024-02-19
You can install the snap:
```
sudo snap install chromium
```

Also, 16.04 proper still receives security updates (even more so if you enable Pro).

---

### Post by fyfe54 on 2024-02-20
If you want Googleless Chrome(ium) try Vivaldi. [www.vivaldi.com](www.vivaldi.com).  

Their blog has articles on how they degoogle.

---

