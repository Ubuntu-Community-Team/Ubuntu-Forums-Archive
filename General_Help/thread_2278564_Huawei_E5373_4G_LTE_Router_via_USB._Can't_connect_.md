---
title: "Huawei E5373 4G LTE Router via USB. Can't connect to internet anymore"
date: 2015-05-17
forum: General Help
---

### Post by konrad9 on 2015-05-17
I've got Huawei E5373 router/modem connected to my pc via usb. It worked on windows and even on linux for a while but suddenly it says you're offline... And I don't have internet access anymore via usb only through Wi-Fi. I tried to find solution but without any result.. lsusb -v shows it is connected as mass storage device. I have no idea what to do. Help me please. Thanks in advance.

I found workaround for this problem:
lsusb to find vendor id and product id and then type
sudo usb_modeswitch -J -v <your vendorid> -p <your product id>

-J is a switch for newer huawei devices

---

