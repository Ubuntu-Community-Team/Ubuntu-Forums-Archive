---
title: "Uninstalling Tor + Privoxy = broken firefox :-("
date: 2007-05-31
forum: General Help
---

### Post by Banter on 2007-05-31
I wanted to have tor and privoxy. So, I installed each of them (via synaptic) plus the torbutton for firefox. I soon after uninstalled them. Now, firefox will not load any pages! I actually have to go back to synaptic and install them to get firefox to work. Has this happened to anyone before?

---

### Post by happy-and-lost on 2007-05-31
I guess deleting the .mozilla folder in your /home (make sure you fish any valuable data like bookmarks out first), and:

```
sudo apt-get install -f firefox --reinstall
```

Should force a reintallation of the 'Fox.

---

### Post by flyingbrass on 2007-05-31
Remove the torbutton thing and check the proxy (network connection) settings in Firefox.  It was probably still set to use port 8118 on your computer.  Select "direct connection."

---

### Post by Banter on 2007-05-31
Firefox was set to still use the proxy. Thanks!

---

