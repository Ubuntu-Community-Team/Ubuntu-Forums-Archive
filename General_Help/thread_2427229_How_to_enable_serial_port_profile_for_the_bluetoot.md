---
title: "How to enable serial port profile for the bluetooth service on ubuntu 18.04"
date: 2019-09-19
forum: General Help
---

### Post by lambyxq on 2019-09-19
Dear all,


After I recomplied the kernel and enabled rfcomm support in the kernel setting on my micro controller (Jetson Nano which runs ubuntu 18.04) , I could create "/dev/rfcomm0" serial port now by using the command "sudo rfcomm bind 0 00:04:3E:4B:32:40".


However, when I tried to read the data from externel bluetooth sensor by the python script, the error returned which said "could not open /dev/rfcomm0 port". 


I tried to edit /etc/systemd/system/dbus-org.bluez.service file like below which worked for my raspberry pi 3b+.


ExecStart=/usr/lib/bluetooth/bluetoothd -C
ExecStartPost=/usr/bin/sdptool add SP


However,after I reboot the microcontroller, the bluetooth service failed to start. Because there is no embedded bluetooth module on the microcontroller, I used the externel bluetooth adapter for my microcontroller. The bluetooth logo is on the the desktop and I could scan the bluetooth devices by this adapter. 


What should I do? I could recompile the kernel but I don't know which setting could enable serial port profile for the bluetooth service on unbuntu18.04. Any suggestions would really be appreciated.


Best regard,
Xiaoqun Yu

---

### Post by lambyxq on 2019-09-19
Hi,


I found the solution was quite easy. After we create "dev/rfcomm0", before we run the script to read data, we need to "sudo chmod 777 /dev/rfcomm0", then the port could be open. It was so different with raspberry Pi.




Best regard,
Xiaoqun Yu

---

