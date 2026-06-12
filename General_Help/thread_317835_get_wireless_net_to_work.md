---
title: "get wireless net to work?"
date: 2006-12-13
forum: General Help
---

### Post by andsch on 2006-12-13
I cant get the wireless internet to work in ubuntu... in windows i HAD a driver called "broadcom wireless ulity"...:confused:

---

### Post by Laryllan on 2006-12-13
Search the forums and the Wiki for help.
There are many posts and articles about WLAN and Linux.

---

### Post by strabes on 2006-12-13
```
sudo ifconfig eth1 up
sudo apt-get install network-manager-gnome
nm-applet &
```

Connect to the wifi network, and paste this command:

```
sudo dhclient eth1
```

---

