---
title: "Need help finding network driver smc2-1211tx"
date: 2006-11-16
forum: General Help
---

### Post by sibaroochi on 2006-11-16
I am a beginner and can not find a driver anywhere for this network card:

Accton Technologies smc2-1211tx


Any help is appreciated!

---

### Post by Joe_CoT on 2006-11-16
According to [this](http://www.rockhopper.dk/linux/hardware/network_cards.html), it's a standard realtek network card. Pretty sure it's in ubuntu as a module.

try this:
```
sudo modprobe 8139too
```

if that works, you can add it to your /etc/modules file to load it on startup

---

### Post by sibaroochi on 2006-11-18
Thanks for the answer. I am very new to installing drivers and don't know how to set it up. even the instructions at the link you sent me is confusing me. I will try to read up on the manuals and get more acquainted with this OS.

Thanks :-?

---

### Post by Joe_CoT on 2006-11-18
The site I linked to wasn't meant to be instructions, just documentation as to where i got my answer. As I said, all you need to do is this from a console:

```
sudo modprobe 8139too
```

Which will load the needed module. Then try configuring your network card. If that works
```
sudo nano -w /etc/modules
```
and add "8139too" on another line, and save. that way it'll get loaded with ubuntu.

---

