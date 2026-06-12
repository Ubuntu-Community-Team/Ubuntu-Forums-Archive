---
title: "Tusk Software Deosn't Run"
date: 2024-06-18
forum: General Help
---

### Post by webmanoffesto on 2024-06-18
I am an Evernote user. I was hoping Tusk would be a good alternative to NixNote. I installed Tusk from "Ubuntu Software". It seems to have installed. In the software store it shows as "installed". I can SuperKey and type Tusk and the Start Tusk icon appears. But when I click on the icon the software doesn't start. How can I fix this problem?

$ tusk
Gtk-Message: Failed to load module "appmenu-gtk-module"
$ sudo apt-get install appmenu-gtk2-module appmenu-gtk3-module
[sudo] password for _____
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
appmenu-gtk2-module is already the newest version (0.7.6-2).
appmenu-gtk3-module is already the newest version (0.7.6-2).
0 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.




Ubuntu 22.04
HP Laptop

---

### Post by Holger_Gehrke on 2024-06-18
Since tusk isn't in the repositories, that means you probably installed a snap. Since snaps are isolated from the rest of the system installing a needed piece of software through apt won't help. Have you tried installing either the AppImage or the .deb package from the release page of the github ([https://github.com/klaudiosinani/tusk/releases/tag/v0.23.0](https://github.com/klaudiosinani/tusk/releases/tag/v0.23.0)) ?

Holger

---

