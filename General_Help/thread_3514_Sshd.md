---
title: "Sshd"
date: 2004-11-06
forum: General Help
---

### Post by Franz on 2004-11-06
Hi People,
I can't launch sshd and, if I try to do "apt-get install ssh", it doesn't install anything from the net and it requests the Ubuntu Cd. Can anyone help me?
Thanks :-D

---

### Post by CapKrugers on 2004-11-06
You could edit /etc/apt/sources.list to exclude the CD-ROM by commenting it out and then apt-get. Or you could try /etc/init.d/sshd stop and then /etc/init.d/sshd start (IIRC; I m n00b)

With Synaptic you can easily enable/disable repositories in a menu.

---

### Post by WW on 2004-11-06
The package that you want to install is **openssh-server**:

```
sudo apt-get install openssh-server
```

If it asks for the CD, you could either (1) put the in the CD :), or (2) remove the CD from sources.list.  To do that, either edit /etc/apt/sources.list and comment out the CD line, or use synaptic to disable the CD-based repository.  Then apt-get update (or hit Reload in Synaptic) before trying to install openssh-server.

---

