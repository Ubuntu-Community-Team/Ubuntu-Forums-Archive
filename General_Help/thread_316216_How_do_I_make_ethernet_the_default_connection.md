---
title: "How do I make ethernet the default connection?"
date: 2006-12-10
forum: General Help
---

### Post by viciouslime on 2006-12-10
I recently had a problem with my router and so I used my laptop as a temporary replacement for it using a usb speedtouch adsl modem. I followed the guide in the ubuntu wiki ([https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch](https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch)) and all worked very well.

However, I have now sorted the problem by fixing my spare router, however now  I can't get my laptop to access the web. Can anyone tell me how to reverse the last part of the guide:

The Ethernet Issue

If you have an ethernet connection at installation,Ubuntu makes it the default connection, we don't want that, so we do the following:

sudo sed -i 's@gateway@# gateway@g' /etc/network/interfaces &&
sudo sed -i 's@dns@# dns@g' /etc/network/interfaces &&
sudo rm -f /etc/resolv.conf

Thanks in advance!

---

### Post by Ramses de Norre on 2006-12-10
This will undo the sed commands:
```
sudo sed -i 's/# gateway/gateway/g' /etc/network/interfaces
sudo sed -i 's/# dns/dns/g' /etc/network/interfaces
```

You also need to make an /etc/resolv.conf and put your dns servers in it, like this: ```
nameserver xxx.xxx.xxx.xxx
```

---

### Post by viciouslime on 2006-12-10
Thank you! :D

---

