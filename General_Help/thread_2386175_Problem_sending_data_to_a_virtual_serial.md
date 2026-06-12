---
title: "Problem sending data to a virtual serial"
date: 2018-03-01
forum: General Help
---

### Post by josiperez on 2018-03-01
Hi,

I have a hardware that simulates a virtual serial: it connects with the Windows computer via USB and my software sends signals to this hardware via COMx port; in Windows there is an utility that indicates what serial port has been used. Worked.


My problem arises when I try to do the same in an Ubuntu 16.04 environment, where my software really needs to run.
When I connect the hardware via USB in an Ubuntu machine, the system recognizes the new hardware with dmesg; usbview also shows product and vendor correct names.


In /dev listing there is no one /dev/ttyUSBx (where I think that should appear) and no other new device, then I created it manually, using data from dmesg and lsusb:
sudo modeprobe usbserial vendor=0x1103 product=0x0021


Appears: ttyUSB0 and ttyUSB1
Seted dialout permission and rw permission.
I tried:
1) to send signals inside my software to "/dev/ttyUSB0" and USB1, without success. Nothing.
2) to send manually to the port using: sudo echo "0x03" > /dev/ttyUSB0 and USB1 - nothing
3) minicom - nothing
4) moserial, defining 9600 8N1 - nothing

Someone could give me an idea about what is wrong with my tests?
Directions?

I thought to install wine, but, the software needs to run in unix to avoid delays, and probably wine generates delays, right?

Thanks in advance,
Josi Perez

---

### Post by HermanAB on 2018-03-01
It means that the device you are using is not supported and a device driver is not loaded.  You can list the device drivers with lsmod.

Try devices from [http://serialcom.com](http://serialcom.com), they work well on any computer system.

There are lots of serial port tips on my web site, since it is a permanent head-ache in my line of work!
[www.aeronetworks.ca/2015/01/serial-port-io.html](www.aeronetworks.ca/2015/01/serial-port-io.html)
[www.aeronetworks.ca/2014/10/serial-ports-revisited.html](www.aeronetworks.ca/2014/10/serial-ports-revisited.html)
[www.aeronetworks.ca/2014/01/crcs-and-serial-ports.html](www.aeronetworks.ca/2014/01/crcs-and-serial-ports.html)
[www.aeronetworks.ca/2013/10/serial-port-tricks.html](www.aeronetworks.ca/2013/10/serial-port-tricks.html)
[www.aeronetworks.ca/2013/05/usb-serial-device-with-unknown-ids.html](www.aeronetworks.ca/2013/05/usb-serial-device-with-unknown-ids.html)
[www.aeronetworks.ca/2015/10/reading-and-parsing-data-from-serial.html](www.aeronetworks.ca/2015/10/reading-and-parsing-data-from-serial.html)
[www.aeronetworks.ca/2013/05/compile-moxa-serial-widget-device.html](www.aeronetworks.ca/2013/05/compile-moxa-serial-widget-device.html)
etc...

---

### Post by josiperez on 2018-03-02
Herman, thank you very much for your answer and suggested links.

The answer to "cat /dev/ttyUSB0" (after stty -F /dev/ttyUSB0 raw; stty -F /dev/ttyUSB0 9600) is always small squares with 00 in first line and 02 in the second. I don't know what is this.
I will try the script "echo and read"described in serial-ports-revisited.

I can't choose the device: it is part of an EEG system: there is an scalp EEG connected to an amplifier and the amplifier connects to a PC with a software that receives the EEG waves and the triggers sended by any other software. The amplifier do not have all kind of ports, then, it has an "input port" that connects with the device TriggerBox. This TriggerBox has the USB port to connect with my program. Sorry for the blablabla, but I am not experienced in this type of stuff then I need to explain to my brain...

I think I am doing something wrong because I should to see something being sended - wrong, but something. Right?
Is it correct that I should use the ttyUSB because the hardware was recognized by lsusb?
The people that will analyze the results needs precision - then, using wine software it is wrong, because it is a new layer to give delays. Right?

Some tips?

[COLOR=#000000]Thanks in advance,[/COLOR]
[COLOR=#000000]Josi Perez[/COLOR]

---

### Post by josiperez on 2018-03-02
```
$ cat /proc/tty/drivers
/dev/tty             /dev/tty        5       0 system:/dev/tty
/dev/console         /dev/console    5       1 system:console
/dev/ptmx            /dev/ptmx       5       2 system
/dev/vc/0            /dev/vc/0       4       0 system:vtmaster
usbserial            /dev/ttyUSB   188 0-511 serial
rfcomm               /dev/rfcomm   216 0-255 serial
ttyprintk            /dev/ttyprintk   5       3 console
max310x              /dev/ttyMAX   204 209-224 serial
serial               /dev/ttyS       4 64-111 serial
pty_slave            /dev/pts      136 0-1048575 pty:slave
pty_master           /dev/ptm      128 0-1048575 pty:master
unknown              /dev/tty        4 1-63 console
```

```
:/sys/bus/usb/drivers/usbserial_generic$ ls -latotal 0
drwxr-xr-x  2 root root    0 Fev  5 19:43 .
drwxr-xr-x 11 root root    0 Fev  5 19:43 ..
lrwxrwxrwx  1 root root    0 Fev  5 19:44 2-1.2:1.0 -> ../../../../devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.2/2-1.2:1.0
lrwxrwxrwx  1 root root    0 Fev  5 19:44 2-1.2:1.1 -> ../../../../devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.2/2-1.2:1.1
--w-------  1 root root 4096 Fev  5 19:44 bind
lrwxrwxrwx  1 root root    0 Fev  5 19:44 module -> ../../../../module/usbserial
--w-------  1 root root 4096 Fev  5 12:50 uevent
--w-------  1 root root 4096 Fev  5 19:44 unbind
```

---

### Post by HermanAB on 2018-03-02
You can see which USB serial devices are there with:
$ ls /dev/ttyU*

Loop Tx to Rx (pins 2 and 3) with a paper clip or little wire and use cutecom to verify that it works.

---

### Post by josiperez on 2018-03-02
Thank you again HermanAB.

I can see /dev/ttyUSB0 and /dev/ttyUSB1, but not after plug the device - after execute a modprobe: the two ttyUSBx gave birth at same time.
I wil digest the instruction "loop tx to rx".
Thanks.
Josi

---

### Post by QIII on 2018-03-02
Hello, josiperez!

Welcome to the Forums!

Please use code tags to contain all terminal commands and their results. That preserves terminal formatting and makes your posts much easier to read.

To use code tags, you may either:

Highlight text and click the # button in the text box header or click the # button first, place your cursor between the code tags and type or paste your text.

- or -

Type [noparse]```
[/noparse] at the beginning of your text and [noparse]
```[/noparse] at the end. The square brackets are required.

Please also use the default font unless there is some reason to draw attention to a specific portion of your post.

Thanks!

---

### Post by josiperez on 2018-03-02
Sorry QIII and readers.
I will pay attention next time.
Josi

---

