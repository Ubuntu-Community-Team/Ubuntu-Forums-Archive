---
title: "problems starting admin applications"
date: 2006-09-27
forum: General Help
---

### Post by jdrott1 on 2006-09-27
cant't start administrative applications. As soon as it starts it disappears.
i've tried these solutions with no luck. my computer doesn't allow me to sudo nano /etc/hosts in recovery mode. my hostname is (none).

this is what message i'm getting:

jonathan@(none):~$ gksudo synaptic
sudo: unable to lookup (none) via gethostbyname()

---

### Post by ayoli on 2006-09-27
in recovery mode you _are_ root, so you don't need sudo to edit /etc/hosts and /etc/hostname in this mode.
you need a hostname in /etc/hostname and a line in /etc/hosts like this:
> 127.0.0.1 localhost *your_hostname*

---

