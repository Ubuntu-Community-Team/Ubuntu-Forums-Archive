---
title: "Can't print"
date: 2012-12-18
forum: General Help
---

### Post by Welly Wu on 2012-12-18
I have a System76 Lemur Ultra Thin (lemu4) with Ubuntu 12.10 64 bit and I also have a Canon Pixma MX870 all-in-one multi-function printer. I connected it using the Category 5e cable and it is connected at 192.168.1.9. I successfully added IPP port 631 TCP and port 631 UDP using GUFW. I can add my printer, but I can not print to it. I keep getting a printer not connected error. I already installed the Canon Europe drivers using a modified install.sh script, but it fails to find my printer on my network.

How do I solve this problem so that I can print to my printer?

---

### Post by Ms. Daisy on 2012-12-18
Have you tried to print when the firewall was disabled? If it's successful then you know it's a firewall problem. If you can't print even without a firewall then it's likely a CUPS or driver issue.

---

### Post by Welly Wu on 2012-12-19
I'll try out your suggestions later tonight.

---

