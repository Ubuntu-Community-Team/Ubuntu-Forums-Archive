---
title: "What's the best way to disable menus and applications?"
date: 2008-05-24
forum: General Help
---

### Post by ruipedroca on 2008-05-24
Hi,

My question is simple: 
I need to setup several desktop pc's with ubuntu 8.04 and i need to:

a-to lock down menus, so that users just can browse through a list of predefined menus and thus launch only predefined programs
b-can't connect usb pen or usb drives
c-can't have access to terminal, network nor any other settings (like desktop, display, mouse, etc)
d-just could save data in their homes directory


Users must only use the following software:

1-openoffice
2-image editor (gimp is just fine)
3-pdf viewer
4-pdf printer
5-mpeg or divx player, nothing fancy, just a very simple player
6-browser to browse only internal site, mozila is just fine
7-scanner software
8-ability to connect photo digital camera
9-samba, nfs and ftp client


What's the best way to accomplish this? 
Is there any GUI?


Thanks in advance!

---

### Post by PinkFloyd102489 on 2008-05-24
Right click on the menu button and select Edit Menus. Then just check/uncheck what you want/dont want.

---

### Post by ruipedroca on 2008-05-24
Hi, PinkFloyd102489!

Thanks for your reply!
That works, but how can i prevent users from editing the menus also?

Regards!

---

### Post by Forlong on 2008-05-25
The settings get stored in the (hidden) .config directory of the respective home directory.

Thus, you could prevent from changing those like this:
```
sudo chown root:root $HOME/.config/menus/
```

---

### Post by ruipedroca on 2008-05-26
Hi, Forlong!

Thanks!

---

