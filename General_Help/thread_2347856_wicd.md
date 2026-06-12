---
title: "wicd"
date: 2016-12-29
forum: General Help
---

### Post by pete1977x on 2016-12-29
i run xfce in ubu 14.4
as usual the wifi icon screws up. I finally got something in the tray by installing wicd. Can I now uninstall network-manager?  I dont need 2 services going at one time,no??
sud apt-get rm network-manager
 is this correct terminal code??

---

### Post by TheFu on 2016-12-29
yes. remove nm-*  I don't have network-manager on any of my systems. I think it gets confused by non-trivial networking.  I only use wicd-curses for wifi management. Never for ethernet-cable connections.

[https://help.ubuntu.com/14.04/serverguide/apt-get.html](https://help.ubuntu.com/14.04/serverguide/apt-get.html)
[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

apt, aptitude, apt-get each have slightly different uses.  For example, aptitude has a curses TUI.  apt-get can do simple wildcard pattern matching. apt is the newest tool.

That command above it NOT correct. details matter. 2 mistakes.

---

### Post by pete1977x on 2016-12-29
whats the correct code to uninstall NM

---

### Post by howefield on 2016-12-29
```
sudo apt remove network-manager
```

or

```
sudo apt purge network-manager
```

see

```
man apt-get
```

for the difference between remove and purge.

---

