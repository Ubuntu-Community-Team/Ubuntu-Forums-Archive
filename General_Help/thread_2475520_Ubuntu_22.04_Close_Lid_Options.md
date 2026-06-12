---
title: "Ubuntu 22.04 Close Lid Options"
date: 2022-05-30
forum: General Help
---

### Post by agentl074 on 2022-05-30
How do I change the close lid options in Ubuntu 22.04? Thanks!

---

### Post by #&amp;thj^% on 2022-05-30
have a look in:
```
cat /etc/systemd/logind.conf
```
To change lid close action without any condition, enable the #HandleLidSwitch=suspend line and change the value to ignore, lock, poweroff, etc.
After any changes you will to run:
```
systemctl restart systemd-logind.service
```

---

### Post by agentl074 on 2022-05-30
Thank you! Would the OS automatically switch modes if it detects an external monitor attached (command center)?

---

### Post by #&amp;thj^% on 2022-05-30
Depends, try it and see. Wayland and Xorg have some differences in how or if they react to a hot plug.

---

### Post by agentl074 on 2022-05-30
I actually solved the problem via installing Gnome Tweaks :) Thank you for your assistance :)

---

### Post by #&amp;thj^% on 2022-05-30
Good to know, I don't use many GUI's
Regards

---

### Post by agentl074 on 2022-05-30
I don't blame you at lol lol. Things can be done much faster and more efficiently via command :)

---

