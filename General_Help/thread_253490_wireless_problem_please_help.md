---
title: "wireless problem please help"
date: 2006-09-08
forum: General Help
---

### Post by amirji on 2006-09-08
im trying to search for wireless connections, when i switch my wireless on, what do i do? in windows all u do is go to net conns and search for signals, i have tried using airsnort, but when i click start, terminal displays a message, i have the screenshot. please help coz i will be taking my laptop to  university, not much good if it dont pick up signals :(

---

### Post by amirji on 2006-09-08
bump

---

### Post by Iwantu_ubuntu on 2006-09-08
Try installing the Network Manager Program. I just installed it on my laptop yesterday but haven't tried it at home yet. I know it works because it displays several WAPs at my office.

sudo apt-get install network-manager-gnome

(Someone correct me if the above is wrong)

---

### Post by noof on 2006-09-08
> **Iwantu_ubuntu said:**
> Try installing the Network Manager Program. I just installed it on my laptop yesterday but haven't tried it at home yet. I know it works because it displays several WAPs at my office.

sudo apt-get install network-manager-gnome

(Someone correct me if the above is wrong)

No, that's right. It'll give you a nice little tray icon that shows the networks when you click it, like:

---

### Post by UltraMathMan on 2006-09-08
You may want to find out what kind of encryption / authentication your University uses, mine uses 802.1x w/ PEAP and if that's the case you'll need to do additional configuration to get it working.

---

