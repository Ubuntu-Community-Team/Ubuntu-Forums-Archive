---
title: "Screen config and networking lost"
date: 2015-07-31
forum: General Help
---

### Post by martinmassera on 2015-07-31
Hi! I need help
I don't know what happened, I turned on my ubuntu laptop as always and the screen resolution is off, displaying 1024x768 on a 1366x768 screen, and also networking is lost, no wifi or ethernet working whatsoever, I execute ifconfig and I only get the self loop interface... 

any ideas how to restore those settings? The computer is fine because I m writing this from my windows partition in dual boot... 

thank you very much to get me through this, I NEED my ubuntu, I just cant do it on windows anymore

---

### Post by shidrang on 2015-07-31
Hi
do you see any error in dmesg output? do you check your runlevel and service --status-all?

---

### Post by martinmassera on 2015-07-31
Hi thanks for answering

I m getting this in dmesg:
PCCT header not found
ACPI PCC probe failed

all rest seems normal. Runlevel is "N 5" and services, not really sure what is ok but networking is on.

Any ideas?

---

### Post by shidrang on 2015-08-01
because of "PCCT header not found" I think you update your system! its seems you update your system or install new app or a driver. please check it.
and for "ACPI PCC probe failed" try:
sudo systemctl enable sddm.service -f
sudo reboot

and also check your /var/log . you can find syslog, try restart your networking service and check for log error.

---

