---
title: "No startup display with Xubuntu 7.10"
date: 2007-11-10
forum: General Help
---

### Post by rogblake on 2007-11-10
I recently decided to give Xubuntu 7.10 a try on an old Compaq Evo n600c laptop which was previously running Xubuntu 7.04. (A complete new installation was done, not an upgrade.)

What's happening is that there is no visual display of bootup progress after the grub menu. While starting up, the screen just goes blank until the login screen appears, after which everything works normally. That is until shutdown, where once again there is no progress screen displayed while the system closes down.

This did *not* occur with version 7.04, and it's pretty annoying. How can I get the startup/shutdown display working? (I don't necessarily need the graphical display, just the standard ASCII listing of services as they fire up or terminate would be fine.)

---

### Post by bionnaki on 2007-11-10
probably a graphic card driver issue...or issue with xorg.conf - I dont know. but to show a text bootup, edit /boot/grub/menu.lst

open terminal

sudo nano /boot/grub/menu.lst

and scroll down to your kernel that you boot into..and delete "silent" from the kernel line. save and reboot.

---

