---
title: "ubuntu 16.04 long booting time"
date: 2016-08-08
forum: General Help
---

### Post by ay91 on 2016-08-08
Hi, 

This is my first post here. I recently upgraded to ubuntu 16.04 and the extra long booting time is really painful. On average it takes more than 2 mins to boot compared to less than 20 seconds in the previous version. I have attached the systemd details here. I am not sure what exactly caused the slow boot. Would appreciate some assistance on this. Thanks!

 13.893s [email]postgresql@9.5-main.servic[/email]e
         13.747s grub-common.service
         13.449s networking.service
         11.405s apport.service
         11.359s irqbalance.service
         11.269s ondemand.service
         11.215s sysstat.service
         11.076s speech-dispatcher.service
         10.972s lightdm.service
          7.811s NetworkManager-wait-online.service
          7.809s dev-sda6.device
          5.821s ModemManager.service
          5.265s apparmor.service
          4.233s accounts-daemon.service
          4.177s NetworkManager.service
          3.192s console-setup.service
          3.143s apache2.service
          2.542s thermald.service
          2.459s systemd-udevd.service
          2.419s polkitd.service
          2.390s gpu-manager.service
          1.938s bluetooth.service
          1.624s avahi-daemon.service

---

### Post by claracc on 2016-08-09
We need more information in order to help.

Hardware specifications: CPU processor, ram, graphics card....

In this thread, [https://ubuntuforums.org/showthread.php?t=1206003](https://ubuntuforums.org/showthread.php?t=1206003), you have some comands to run in order to get your HW specifications.

Also, in a xterm, you can run the comand:

dmesg| less

in order to see the time sequence of booting, on the left of each line, there is time. There you can look for big gaps of time and post here, to give more information.

---

