---
title: "Can't open synaptic package manager due to install crash"
date: 2007-09-19
forum: General Help
---

### Post by durkhrod chogori on 2007-09-19
I tried to install Picasa, the file was corrupted, so I didn't install and when I tried to open "Synaptic Package Manager" I get this message:

[[img]http://xs119.xs.to/xs119/07383/Screenshot.png[/img]](http://xs.to)

Can anyone help me get rid of that mess left by the partial install?


Thanks.

---

### Post by dcstar on 2007-09-19
> **durkhrod chogori said:**
> I tried to install Picasa, the file was corrupted, so I didn't install and when I tried to open "Synaptic Package Manager" I get this message:
........
Thanks.

In a terminal, try:
```
sudo apt-get check
```
Then see if Synaptic works again.

---

