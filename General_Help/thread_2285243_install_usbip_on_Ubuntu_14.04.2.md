---
title: "install usbip on Ubuntu 14.04.2"
date: 2015-07-04
forum: General Help
---

### Post by tbaror on 2015-07-04
Hello

i am trying to install usbip on Ubuntu 14.04.2 server ,I did the following

 ```
apt-get install usbip
```

 , all going well 
Next when i am i trying to install the driver by running 
```
modprobe usbip
```

I get following error ```
modprobe: FATAL: Module usbip not found.
```

Any idea how to fix this ?

Please advice

Thanks

---

### Post by Yellow Pasque on 2015-07-04
Pretty sure you want:
```
sudo modprobe -v usbip-host
```

In the future, you can see avaliable module names by using automatic complete (type the first few letters and hit tab twice).
```
# modinfo usb
usb3503            usb-common         usb_gigaset        usbip-host         usblp              usb-otg-fsm        usbsevseg          usbtouchscreen     usb_wwan           
usb8xxx            usbcore            usbhid             usblcd             usbmon             usbserial          usb-storage        usbtv              
usbatm             usb_debug          usbip-core         usbled             usbnet             usb-serial-simple  usbtmc             usbvision
```

---

### Post by tbaror on 2015-07-04
Thanks):P

---

