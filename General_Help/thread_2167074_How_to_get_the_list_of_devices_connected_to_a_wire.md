---
title: "How to get the list of devices connected to a wireless hotspot?"
date: 2013-08-12
forum: General Help
---

### Post by community on 2013-08-12
Recently I created a wireless hotspot from an ubuntu machine having wired internet connection. I was able to transfer files and share internet with another ubuntu machine with the help of this hotspot. I just need to know, how to get the list of users/devices connected to this hotspot from the machine which created the hotspot(via command-line or GUI)? I don't know whether it is easy or not. Please tell me some solution...

---

### Post by community on 2013-08-16
One way is to look into the network section in nautilus and check the users connected. If Samba is installed Windows machines are also shown. Any other method?

---

### Post by asus-user on 2014-02-10
> **community said:**
> One way is to look into the network section in nautilus and check the users connected. If Samba is installed Windows machines are also shown. Any other method?

I think you can use nmap:

```
sudo apt-get install nmap
```

you can find more information related to this [here]("http://itsfoss.com/how-to-find-what-devices-are-connected-to-network-in-ubuntu/").

---

