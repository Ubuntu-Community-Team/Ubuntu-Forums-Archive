---
title: "No info at start up or shutdown kubuntu 6.10"
date: 2006-11-29
forum: General Help
---

### Post by nignasi on 2006-11-29
Hi,

I'm new to kubuntu: I made a fresh install of Kubuntu 6.10 in two computers. When I switch on the system and select Kubuntu, nothing is shown in my display until the login window excep a blinking underscore. It takes more than two minutes two show anything although the disk is working. Something similar happens
when shutting down or rebooting, the disk is working but the display is black. If I select the 'secure ubuntu' I can see starting up information until login line.

Is anything wrong? 

Ignasi

---

### Post by cronholio on 2006-11-29
Try editing /boot/grub/menu.lst and remove "splash" for the kernel you are booting (usually the top one in the list that is at the end of the file). Backup menu.lst first.

---

