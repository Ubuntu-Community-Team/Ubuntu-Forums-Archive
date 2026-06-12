---
title: "Help about USB GSM Device"
date: 2013-10-31
forum: General Help
---

### Post by efuzone2 on 2013-10-31
I have 2 gsm devices they showed in lsusb but not showing in dmesg | grep ttyUSB


when i manually run this command:


modprobe option


echo 2001 a706 > /sys/bus/usb-serial/drivers/option1/new_id
echo 07d1 7e11 > /sys/bus/usb-serial/drivers/option1/new_id


then it shows in dmesg, please tell me what is wrong and why i have to do this after every reboot and i was seeing people's devices direct shows there please if there is anything let me know...

---

