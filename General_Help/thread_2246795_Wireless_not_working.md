---
title: "Wireless not working"
date: 2014-10-03
forum: General Help
---

### Post by chibi2 on 2014-10-03
I have just installed Ubuntu 14 on my Lenovo IdeaPad Z410. The problem is Wi-Fi is not working at all and even in network settings I don't see wireless option.
Network controller: Broadcom BCM43142 802.11b/g/n [14e4:4365]. How to fix this problem?

---

### Post by varunendra on 2014-10-05
Welcome to the forums chibi2,

Do you have a wired connection or any other method to connect to internet available? If yes, please install the driver that the "Additional Driver" program suggests. Or, in a terminal (that you can open with Ctrl-Alt-T), run the following command to install it -
```
sudo apt-get install bcmwl-kernel-source
```

---

