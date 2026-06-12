---
title: "udev rule file not working"
date: 2013-02-23
forum: General Help
---

### Post by stepheny on 2013-02-23
I am trying to connect an IOIO board (sort of an Arduino for Android) to my Ubuntu 12.04 laptop via a USB connection so that I can program it with Eclipse and the Android SDK.

The rules file is called 50-ioio.rules and the the text is:

```
ACTION=="add", SUBSYSTEM=="tty", SUBSYSTEMS=="usb", ATTRS{idVendor}=="1b4f", ATTRS{idProduct}=="0008", SYMLINK+="IOIO%n", MODE="666"
```

I copied this file to the udev rules directory using:
  
```
sudo cp 50-ioio.rules /etc/udev/rules.d
```

I then restarted udev using:

```
sudo restart udev
```

However when I connect the IOIO board via a USB cable and look for the serial port with 

```
ls /dev/IOIO*
``` 

I get the message 

```
ls: cannot access /dev/IOIO*: No such file or directory
```

Can anyone explain what I am doing wrong?

---

### Post by dagarild on 2013-04-15
I had the same issue, and was unable to get any reading on the USB connection from "tail -f /var/log/syslog".
 I solved this by connecting the IOIO to my computer using a USB cable intended for my phone instead of the one shipped with the IOIO.
Running "tail -f /var/log/syslog" will now output information when connecting the IOIO, and I'll find the IOIO at /dev/IOIO1

---

