---
title: "cd wont run"
date: 2007-09-03
forum: General Help
---

### Post by jnr718 on 2007-09-03
I need help. I don't know very much about this OS. I needed an OS and couldn't afford the 1or2 hundred dollars for windows so I thought Id give this a try. So far its been good. But right now I need to run this cdrom for some home work and it wont run. Should it auto run or what?

---

### Post by ray bot on 2007-09-06
The autorun program on the cd was probably written for Windows.  If you want to run it in Ubuntu, you'll need to install wine.  Open a terminal and type ```
sudo apt-get install wine
```Once that finishes, you should be able to manually run the software on the cd.

---

### Post by Inxsible on 2007-09-06
If the software on the CD was built for Windows it wont run in Linux. Wine might help, but if the software is proprietary and one of a kind, then even Wine would not be of much use :(

I think VirtualBox or VMWare would be of more help !

---

