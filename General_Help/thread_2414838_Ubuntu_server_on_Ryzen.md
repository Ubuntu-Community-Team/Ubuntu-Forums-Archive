---
title: "Ubuntu server on Ryzen?"
date: 2019-03-15
forum: General Help
---

### Post by mattiash on 2019-03-15
I'm trying to install ubuntu server 18.04.2 onto a system with Asus B450 and a Ryzen 2200G. 
The system boots but it goes black a few seconds after I chose to install the server. What to do?

---

### Post by TheFu on 2019-03-16
I googled: "amd 2200G ubuntu install Asus b450" ... [https://askubuntu.com/questions/1070956/how-well-do-amd-raven-ridge-apus-work-with-linux-now](https://askubuntu.com/questions/1070956/how-well-do-amd-raven-ridge-apus-work-with-linux-now)
nomodeset necessary grub option.

I have an Asus ROG B450-F with a Ryzen 2600 - it has been rock solid and didn't need any special grub options to boot, ever.  So, my guess is that the onboard GPU is the issue.  If the solutions in that and similar links is too much for your current Linux skill, perhaps disabling the onboard GPU and using an older GPU - even a $20 PCI card - will let you get the "server" installed and working.  It isn't like "server" will have a GUI anyway.

---

### Post by mattiash on 2019-03-16
So after a days struggle I have solved it. Installed the Ubuntu server via antoher computer, updated the kernal from 4.15 to 4.20 and updated the drivers to AMD and toggled three things in BIOS.

---

