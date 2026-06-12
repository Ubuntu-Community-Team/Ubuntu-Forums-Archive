---
title: "USB Port Designations"
date: 2012-12-30
forum: General Help
---

### Post by anon_private on 2012-12-30
If I am using two USB ports, for the the OS and the other for data, how can I determine which is which. That is, there designations?

---

### Post by rnerwein on 2012-12-30
> **anon_private said:**
> If I am using two USB ports, for the the OS and the other for data, how can I determine which is which. That is, there designations?
hi
using the command: usb-devices
this command will show you the driver (if it is connected) sitting on it.
on my usb
T:  Bus=02 Lev=02 Prnt=04 Port=01 Cnt=01 Dev#=  6 Spd=480 MxCh= 0
S: Product=FRITZ!WLAN USB Stick N 2.4
I:  If#= 0 Alt= 0 #EPs= 4 Cls=ff(vend.) Sub=00 Prot=00 Driver=carl9170

that's my wlan
cheers

---

### Post by gordintoronto on 2012-12-30
Open a terminal, and enter this command:
sudo fdisk -l
In the first line for each device, it shows the size, such as:
Disk /dev/sdc: 8413 MB, 8413773824 bytes
The OS will typically be on a lower device code, such as sda.

---

