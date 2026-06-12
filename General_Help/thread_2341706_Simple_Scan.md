---
title: "Simple Scan"
date: 2016-10-30
forum: General Help
---

### Post by richard7893 on 2016-10-30
Hello,

So I have the Simple Scan app on my Ubuntu. Whenever I try to scan a document using it I always get an error saying: "Failed to scan: Unable to connect to scanner". I have a wireless Wi-Fi Canon PIXMA MX 492 printer/scanner. I installed a driver from Canon that can detect the scanner but Simple Scan is unable to. I am also able to print wireless. How can this be fixed?

Any help would be appreciated

---

### Post by DieB on 2016-10-30
Hi, normally it should be able to select the scanner via File-Settings and then choose your scanner. However, if this is not possible, according to 'man sane-pixma' you can add the ip-address of your scanner to /etc/sane.d/pixma.conf. Simply type 'sudo nano /etc/sane.d/pixma.conf' in your terminal and then add 'bjnp://youripaddress' to the file (with the appropiate IP-address).

---

