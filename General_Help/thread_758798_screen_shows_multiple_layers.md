---
title: "screen shows multiple layers"
date: 2008-04-18
forum: General Help
---

### Post by stymie61 on 2008-04-18
I went and rebooted my machine today, an AOpen mp-965-d mini computer (intel duo core 2.2gh 1GB ram, 80GB Sata HDD, onboard intel video chipset), and had multiple layers of the log in screen as well as desktop after logging in. It also has six mouse pointers showing.

My question is, can this be fixed without reinstalling? and if so what do I need to do?

thanx in advance for the help
      Dennis

---

### Post by zvacet on 2008-04-18
Ctrl+alt +F2

```
sudo dpkg-reconfigure xserver-xorg
```

select **vesa **driver.After festart you will have basic graphic and then go search for driver fo your video card.

---

