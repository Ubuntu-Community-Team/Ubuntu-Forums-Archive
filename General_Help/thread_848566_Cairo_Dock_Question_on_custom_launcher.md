---
title: "Cairo Dock Question on custom launcher"
date: 2008-07-03
forum: General Help
---

### Post by Apex-jb on 2008-07-03
How can I create a launcher for cairo dock to launch nmap and vmware? For vmware there is the icon under applications that I can drag to cairo dock but I need to open it as root, so right now I just open a terminal and type "sudo vmware". With nmap, it is not even under applications, I have to do "sudo zenmap". Can I create a launcher that will run these commands in a terminal?

---

### Post by Shazaam on 2008-07-03
You shouldn't need to run vmware as root. Can I ask why you are doing that?
As far as launchers, go to the properties of the launcher and add sudo to the start of the command. You can add nmap to the Ubuntu menu list by using System>Preferences>Main Menu and clicking "New Item". Then drag/add it to cairo-dock.

---

