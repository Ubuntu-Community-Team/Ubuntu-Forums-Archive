---
title: "xsane not working in Ubu 15.04"
date: 2015-08-22
forum: General Help
---

### Post by Pedroski55 on 2015-08-22
Hi, I have both Ubu 14.04 and 15.04, the latter just recently installed to test. In 14.04, I got my scanner working by putting this 

#[EPSON L350 Series]) at libusb:004:003

usb 0x04b8 0x08a1 

# And for the scanner module, use the following configuration:
usb /dev/usbscanner0

usb /dev/usb/scanner0

in /etc/sane.d/epson.conf

So when the scanner wouldn't work in 15.04, I did the same. However, xsane finds no scanner.

pedro@pedro-275E4E-275E5E:~$ sudo scanimage -L
[sudo] password for pedro: 
Sorry, try again.
[sudo] password for pedro: 
device `epson2:libusb:004:005' is a Epson PID 08A1 flatbed scanner
pedro@pedro-275E4E-275E5E:~$ 


Any ideas why it won't work&#65311;&#65311;

---

### Post by Pedroski55 on 2015-08-24
If you have this problem, make a text file as root called 40-epson-flatbed-scanner.rules, with the following content

ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="08a1", ENV{libsane_matched}="yes"

save it in /etc/udev/rules.d/

Thank you ferrari in New Zealand!

[http://www.linuxquestions.org/questions/linux-hardware-18/xsane-not-working-in-ubu-15-04-a-4175551470/](http://www.linuxquestions.org/questions/linux-hardware-18/xsane-not-working-in-ubu-15-04-a-4175551470/)

---

