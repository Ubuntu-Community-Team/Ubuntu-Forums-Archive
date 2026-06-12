---
title: "live cd internet connection"
date: 2008-02-22
forum: General Help
---

### Post by mikeml on 2008-02-22
I have no idea how to connect to the internet on the ubuntu live cd. I used the connection wizard thing but it didnt have a wireless setting. I dont know how to use ubuntu or any linux operating system well. i barely know how to use ubuntu so could someone help me out?

---

### Post by gobbles414 on 2008-02-22
mikeml,

Look at the right side of your top panel (taskbar). There should be an icon there that resembles two computers with an orange warning sign on top. Single left-click on that icon, and Ubuntu will present you with a list of available wireless networks. You must be using the Ubuntu 7.10 LiveCD or newer in order to access WPA2 encrypted networks. Please let me know if this solution works for you.

PS: You should connect to your WiFi before you start the installation process, because that will allow Ubuntu to automatically configure your computer's update preferences.

---

### Post by mikeml on 2008-02-22
yea that didnt work

---

### Post by gobbles414 on 2008-02-22
mikeml,

How didn't it work? Was the icon there? Were there any wireless networks in the list? I assume that your Wireless router is broadcasting an SSID...? That is, your wireless network's name is being broadcast so that computers can see it in a list of available wireless networks...

Some WiFi hardware in Ubuntu will only work if you are using a driver from *System => Administration => Restricted Drivers Manager*. Normally, Ubuntu automatically loads your WiFi hardware's restricted driver if it is necessary. Of course, the driver for your particular WiFi hardware may not exist in Ubuntu.

It would be most helpful if you could provide more details on your WiFi hardware. Are you using a laptop or a desktop? Are you using built-in wireless, a wireless card, or a wireless USB adapter? If your wireless hardware is built-in, please provide the brand and model number of your computer. If your WiFi hardware is not built into your computer, please provide the brand and model number for the WiFi hardware itself.

---

