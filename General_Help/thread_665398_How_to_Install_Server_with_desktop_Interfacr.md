---
title: "How to Install Server with desktop Interfacr??"
date: 2008-01-12
forum: General Help
---

### Post by Anwarsha on 2008-01-12
Hi I am Very new to Ubuntu would like to change our Microsoft office server 2003  file server to an linux server. I downloaded the server edition and installed as A LAMP server.
I am not familiar with commend promotes and wanted a window interface so typed the commend install ubuntu desktop, I am getting an error E: the package is not available.
Any help is appreciated.
Thanks

:(

---

### Post by LaRoza on 2008-01-12
```

sudo aptitude install ubuntu-desktop

```

You should post any errors you get, and the code you used.

---

### Post by Anwarsha on 2008-01-13
I was using code sudo apt-get install ubuntu desktop

the above code is working but giving me some other errors. I want reinstall and try again thank you very much for you help:)

---

### Post by phillips321 on 2008-01-13
umm, ubuntu-desktop comes with too many extras that your unlikely to want.

after installing server and getting your command line to get a minimal system with the gnome front end try this
```
sudo apt-get install gnome-core gdm gnome-system-monitor gnome-system-tools xarchiver x-window-system-core synaptic
```

this literally installs a very basic system (think ffox is included at most)

u might get some message about installed themes as it'll try to use the default ubuntu theme but wont find it so will have to revert back to a very basic gnome theme

any issues just pm or message in the post

---

### Post by grahambo2005 on 2008-01-13
I think "E: Package not available" means that apt get is looking in your CD ROM Drive, you can either put the Ubuntu CD in the drive and run the command again or you can remove the E: (CD-ROM) from sources.list file

```
sudo nano /etc/apt/sources.list
```

you should see the entry at the top for E: comment it out but do not Delete it. save and run the command again.

Graham

---

