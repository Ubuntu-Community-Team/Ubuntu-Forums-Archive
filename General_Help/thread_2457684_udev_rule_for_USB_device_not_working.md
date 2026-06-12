---
title: "udev rule for USB device not working"
date: 2021-02-06
forum: General Help
---

### Post by einpreusseinbayern on 2021-02-06
Hi all,
I have a virtual serial USB port via an Arduino that creates a /dev/ttyACM0 and I would like it to get read/write access for everyone.

lsusb:
```
Bus 001 Device 037: ID 2341:8037 Arduino SA 
```

udevadm info gives me:
```
looking at device '/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/tty/ttyACM0':
    KERNEL=="ttyACM0"
    SUBSYSTEM=="tty"
    DRIVER==""
<... two levels further down ...>
looking at parent device '/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1':
    KERNELS=="1-1.1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{bDeviceSubClass}=="02"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{devpath}=="1.1"
    ATTRS{idVendor}=="2341"
....
ATTRS{idProduct}=="8037"

```

so I wrote the following rule in /etc/udev/rules.d/80-EKG.rules:
```
KERNEL=="ttyACM?", SUBSYSTEMS=="usb", ATTRS{idVendor}=="2341", ATTRS{idProduct}=="8037", ACTION=="ADD", MODE="0666"
```

but unfortunately I do not get my "666" access permissions:
```
x@y:/dev$ ls -l ttyACM*
crw-rw---- 1 root dialout 166, 0 Feb  6 23:05 ttyACM0
```

Any ideas what is going wrong?

---

### Post by dinkidonk on 2021-02-07
Is your account member of the dialout group? Test with command "groups", if not member add with "sudo usermod -a -G dialout your-user-name".

---

### Post by einpreusseinbayern on 2021-02-07
No, I am not a member of that group, and although I see that adding me to the group would get me access to the device, I still do not know why my udev rule is not working. And that is what it's for me about, understanding how udev works and how to configure it to my liking.

---

### Post by dinkidonk on 2021-02-07
Mode may be changed after your rule is used, try to set the mode as final with MODE:="0666". You may also want to add either an owner or a group to the rule.

---

### Post by einpreusseinbayern on 2021-02-20
I do not quite see what to change in my original rule. I have a MODE="0666" in there. Or do you mean the := with the colon? Tried, that does not make a difference.

---

