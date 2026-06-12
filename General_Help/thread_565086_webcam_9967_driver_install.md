---
title: "webcam 9967 driver install"
date: 2007-10-01
forum: General Help
---

### Post by marel791 on 2007-10-01
I'm an absolute noob but willing to learn. I managed to find the driver for the webcam I have . The chipset is w9967cf.

my lsusb is:
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 1046:9967 Winbond Electronics Corp. [hex] W9967CF/W9968CF WebCam IC
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000

and similarly my lshw for just the usb is:
*-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:9c00-9c1f irq:19
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Generic USB device
                   product: W9967CF
                   vendor: WINBOND
                   physical id: 1
                   bus info: usb@2:1
                   version: 1.10
                   capabilities: usb-1.10
                   configuration: driver=w9968cf maxpower=500mA speed=12.0MB/s 

I want to know how to install the driver. I read that you have to make sure certain modules are running first. I barely know how to modify directories. Can someone help?

---

### Post by geraldm on 2007-10-01
There is a module in the kernel that has to be loaded.  One way as root load the module:
```

 insmod /lib/modules/`uname -r`/kernel/drivers/media/video/w9968cf.ko 
 tail -n4 /var/log/syslog

```
which shows:
Oct  1 21:20:46 lo kernel: w9968cf: V4L driver for W996[87]CF JPEG USB Dual Mode Camera Chip deregistered
Oct  1 21:22:20 lo kernel: w9968cf: V4L driver for W996[87]CF JPEG USB Dual Mode Camera Chip 1:1.33-basic
Oct  1 21:22:20 lo kernel: usbcore: registered new interface driver w9968cf
r

There is a companion decompression program for this device.  A program to view the
output is also needed.  The device may be available at /dev/video?  (where ? is a number)

Gerald

---

### Post by marel791 on 2007-10-02
insmod told me there was already a file there which is good right? and then tail said this:

Oct  2 16:19:46 computer.name dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Oct  2 16:19:58 computer.name dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Oct  2 16:20:03 computer.name dhclient: No DHCPOFFERS received.
Oct  2 16:20:03 computer.name dhclient: No working leases in persistent database - sleeping.

and I don't even have a dev/video file....

---

### Post by geraldm on 2007-10-02
The lines that the module writes into the log were not what you displayed.
After loading the module, look in file /var/log/syslog.
There should be at least 3 lines near the end of the file with the letters "w9968cf" in the line.
The module needs to locate a camera to drive, and after that is found, there should be
an entry at /dev/video0 (or some other number in place of 0 )  This information is 
usually written to the log.

Also note that the website states that the last supported linux kernel is 2.6.18 for the
v4l1 (video for linux one interface).  Others may work, but are not supported.

You can check whether the module is loaded with 
```

lsmod | grep "w9968cf" - 

```

Gerald

---

### Post by marel791 on 2007-10-03
w9968cf                72096  0
compat_ioctl32          2304  1 w9968cf
videodev               28160  1 w9968cf
i2c_core               22656  3 i2c_ec,ovcamchip,w9968cf
usbcore               134280  5 w9968cf,usbhid,ehci_hcd,uhci_hcd

That's loaded right? So next is the driver?

---

### Post by geraldm on 2007-10-03
Looks like you got the driver module loaded.  This  module w9968cf has two ways it can be
used.  One way, for low resolution frames, is to use a viewer program, one that handles
v4l1 ((video for linux one).  Just need the viewer.  Camera sends uncompressed frames.

The other way is with w9968cf-vpp (? name).  This program can set the module to use
compressed video, which this program handles, and then decompresses it, and creates
a file stream.  The program should come with some documentation to show how to set
it up.  You would need to read it, as I have not yet looked at it. A viewer is also needed
for this setup.

Do you have enough information to keep at it?  
There is more information at [www.linux-projects.org](www.linux-projects.org).  
That might be a bit hard to understand, as it appears to be written for users who are
fairly advanced.  If you have questions that are not answered, perhaps a more gentle
introduction would need to be written.  I do not have any pointers to such a reference,
though.

Next step is to get a useable viewer, get documentation on how to use it, and enjoy. 

Gerald

---

### Post by marel791 on 2007-10-03
Would Kopete be able to use the file stream?
I think it's enough for now... thanks for all the help geraldm.

---

