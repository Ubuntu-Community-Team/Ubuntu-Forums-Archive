---
title: "Unable To Delete A Folder"
date: 2007-05-16
forum: General Help
---

### Post by Prometheus.172214 on 2007-05-16
Hi,
    I am running Edgy Eft on my system, (Intel X86) with no modifications to the kernel. I recently tried to install Citrix for Linux on this machine, so I could remote login to my office domain and in this process, I somehow ended up creating a folder on my desktop named linuxx86 which is the Citrix folder and the icon for this shows a yellow lock. I cannot delete, rename or move this folder and need you guidance to either move thie or somehow remove Citrix and delete this. I can reinstall Citrix later on the system. Here is how it looks.

[IMG]http://img249.imageshack.us/img249/9926/screenshotcj0.png[/IMG]

The error I get, when I try to delete the folder looks like this.
[IMG]http://img249.imageshack.us/img249/4546/screenshot1iq5.png[/IMG]

:confused:

---

### Post by mills on 2007-05-16
```
cd Desktop
```p

```
sudo rm -R linuxx88
```

i think that should do it

EDIT: capital D on desktop

---

### Post by Prometheus.172214 on 2007-05-16
That did the trick ....... Thanks ...........

:-)

---

### Post by mills on 2007-05-16
dont thank me, thank the guy who wrote the online book in my sig:)

---

