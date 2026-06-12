---
title: "File Transfer Problems"
date: 2007-12-25
forum: General Help
---

### Post by Tristanm1 on 2007-12-25
I have been having problems with file transfers involving anything other than an HTTP or FTP transfer protocols (such as BitTorrent and IRC) I can connect to the trackers and chat rooms, but actually downloading/uploading doesn't happen. I don't have a firewall installed, so there is no reason for this to happen. I know it is my computer as whether I am on UW Parkside's network, or at home, I cannot seem to download. Does anyone know how to fix this?

---

### Post by TidusBlade on 2007-12-26
It could be your router if you have one?

---

### Post by Tristanm1 on 2007-12-26
Other computers on this network are not affected, and my laptop is affected outside of my network, so I don't think it could be.

---

### Post by TidusBlade on 2007-12-26
Hmm, maybe try looking in your firewall if you have one, or opening the needed ports using iptables? 
```
sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT
```
That opens the port 6881.

---

### Post by Tristanm1 on 2007-12-26
As I said, I do not have a firewall, though what port does XChat-Gnome use for file transfers? I'll try opening that up.

---

