---
title: "new ubuntu user"
date: 2007-10-30
forum: General Help
---

### Post by taurusbill on 2007-10-30
Do I need to install a firewall,  I have ubuntu installed on a virtual drive

---

### Post by por100pre1 on 2007-10-30
Welcome to the forums. The system already has a firewall. Install Firestarter to configure it. Copy, paste and ENTER this command in Terminal (**Applications> Accesories> Terminal**):

```
sudo aptitude install firestarter
```

Open it, configure it, and close it. No need to keep it running. I'm not sure if you actually need a firewall.

---

### Post by Tyke91 on 2007-10-30
ubuntu comes with a built in firewall called IPtables. all of the ports should be closed by default, but i have heard other people say that they are always open.

if you want to manage your firewall, i would suggest using firestarter, a graphical tool that you can use. 

you can get firestarter from synaptic or add/remove or ```
sudo apt-get install firestarter
```


EDIT: doh, posted at the same time

---

