---
title: "Default Runlevel"
date: 2008-05-22
forum: General Help
---

### Post by Gauvenator on 2008-05-22
How can I change the default runlevel to 3?

---

### Post by Gauvenator on 2008-05-22
I realize that in other distros you can edit the /etc/inittab, but it doesn't seem to exist in hardy.

---

### Post by pointone on 2008-05-22
Edit "/etc/event.d/rc-default".

---

### Post by Gauvenator on 2008-05-22
ubuntu seems to have a different runlevel system.  I want what usually is runlevel 3 (multiuser, network, command line).  How can I get this?

---

### Post by chrisccoulson on 2008-05-22
In Ubuntu, run-levels 2, 3, 4 and 5 are all the same (multi-user, with GUI)

---

### Post by fsmithred on 2008-05-22
> **Gauvenator said:**
> ubuntu seems to have a different runlevel system.  I want what usually is runlevel 3 (multiuser, network, command line).  How can I get this?

I feel your pain. (old suse and redhat user here)

Leave runlevel 2 as the default, but without gui:

```
sudo update-rc.d -f gdm remove
sudo update-rc.d gdm start 3 4 5 . stop 0 1 2 6 .
```
(Don't forget the dots.)

---

### Post by Gauvenator on 2008-05-22
> **fsmithred said:**
> I feel your pain. (old suse and redhat user here)

Leave runlevel 2 as the default, but without gui:

```
sudo update-rc.d -f gdm remove
sudo update-rc.d gdm start 3 4 5 . stop 0 1 2 6 .
```
(Don't forget the dots.)

Thank you so much!!  That worked perfectly.

---

