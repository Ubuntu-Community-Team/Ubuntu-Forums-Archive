---
title: "What is this error?"
date: 2024-05-05
forum: General Help
---

### Post by amiarg on 2024-05-05
usb 3-10: 3:1: cannot get freq at ep 0x84
I am not sure I understand it correctly, is it referring to Bus 003 Device 010? What is 3:1 and what is ep 84?

---

### Post by Rubi1200 on 2024-05-05
When do you see this error? Does it prevent you from booting to the desktop?

Have you checked BIOS and/or unplugged any external USB devices to check if that resolves the issue?

---

### Post by amiarg on 2024-05-05
It starts in boot, i disconnected a couple of USB devices for reboot and it still showed, I also checked now I do not have anything on Device 010. so 310 is probably not what i thought it was.

---

### Post by Rubi1200 on 2024-05-05
I would say that if you can boot and get to the desktop then it is probably nothing to worry about.

Try running apt update and apt upgrade to see if that resolves the issue.

Also check the logs in case there is something useful to post here.

---

