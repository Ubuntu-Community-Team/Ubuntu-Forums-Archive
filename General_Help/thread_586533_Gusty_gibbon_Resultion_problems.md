---
title: "Gusty gibbon Resultion problems"
date: 2007-10-22
forum: General Help
---

### Post by -gabe-noob- on 2007-10-22
Ok so I turned on my computer this morning and my resultion is somthing like 640x800 I usaly go by alot higher but when I got to custimize it there are no other resultions, what should I do?

---

### Post by Luis_vxd on 2007-10-22
Hi

I had the same problem.
Look into /etc/x11/xorg.conf for 
      HorizSync        28-51
      VertRefresh    43-60

These should be in section "Monitor" after options "DPMS". If not there edit the xorg.conf file and add them. Reboot and should work.

---

### Post by TNakos on 2007-10-22
you need to run a dpkg reconfigure of the xorg xserver file. then fit escape until you get to moniter settings. you can also monkey with the video settings

---

### Post by Luis_vxd on 2007-10-22
I ran "sudo dpkg-reconfigure -phigh xserver-xorg" as the.xorg.conf file says but got nowhere. After reboot the maximum available resolution was 800x600 without the Restricted nvidia driver installed. After driver installation only 640x480.
It didnt make sense as my xorg backup file didnt have sync parameters. Only after several try n error (it took me a whole day) I manage to have the 1024x768 resolution back by adding sync parameters.
Do you have any idea of what was (maybe still is) wrong?

---

