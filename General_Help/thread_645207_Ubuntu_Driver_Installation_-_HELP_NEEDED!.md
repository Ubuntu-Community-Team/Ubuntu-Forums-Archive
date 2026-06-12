---
title: "Ubuntu Driver Installation - HELP NEEDED!"
date: 2007-12-19
forum: General Help
---

### Post by Rusty023 on 2007-12-19
I'm trying to get this driver to work, but I'm afraid it doesn't work with Ubuntu. Can some Ubuntu genius please tell me what I need to do to get this working in Ubuntu? Here's the installation PDF that came on the CD:

```
Installation for the Linux driver
Version 1.0
CONTENTS
A. Requirements and Pre-installation............................................................................2
B. Uncompress the Package...........................................................................................2
C. Build and Install the Package....................................................................................3
D. Install the Driver.......................................................................................................3
E. Check the Driver.......................................................................................................3
F. Configure the Network Interface...............................................................................4
G. Open the Network Interface......................................................................................7
H. Configure the Wireless Settings................................................................................8
Page 1 of 8
A. Requirements and Pre-installation
• The WL230USB driver for Linux distributions works with Kernel 2.4.x and 2.6.x on x86 platforms.
• A 12MB free disk space is needed for the installation.
• You will need: Configured kernel source code for the kernel you are running. Ideally, Configured means that you have at least run “make config”, “make enuconfig”, or “make xconfig”. If your platform is not SMP system, please do not config SMP supported. This is because when module loaded, it will make unresolved symbol.
• Make sure your kernel usb 2.0 support is running;
- Use “lsmod” to check "ehci-hcd" module is loaded.
- If the USB host is not USB 2.0 supported, the Wireless USB adapter will run under pure-b mode (802.11b).
B. Uncompress the Package
• Copy the driver package WL230USBLnxDrv_2_12_0_0.tar.gz under the Linux Driver folder on the CD to the system root directory.
• Decompress the package by using the command:
“tar zxvf WL230USBLnxDrv_2_12_0_0.tar.gz”.
• Change the directory to WL230USBLnxDrv_2_12_0_0 by using the command:
“cd WL230USBLnxDrv_2_12_0_0”.
Page 2 of 8
C. Build and Install the Package
Follow the below commands to build and install the package:
• make clean
• make
• make install
D. Install the Driver
If you are using Kernel 2.4, please use the below command to install the driver:
• insmod WL230USB.o
If you are using Kernel 2.6, please use the below command to install the driver:
• insmod WL230USB.ko
E. Check the Driver
To check whether the driver is loaded successfully, you can use the command: “lsmod”.
If the driver is loaded successfully, the following messages should be seen:
...
WL230USB 294424 0
...
Please note that the 294424 may not be the same as that in your system. You can now plug in the AZTECH WL230USB B+G Adapter.
Page 3 of 8
F. Configure the Network Interface
• Select “Network Card” from the “Network Devices”.
• Select “AZTECH WL230USB B+G Adapter” and click on “Edit”.
Page 4 of 8
Select Device Type as “Wireless”. Under Setup Method, select “Automatic Address Setup (via DHCP)” and click “Next”.
• At the below prompt click Continue.
Page 5 of 8
• Configure your wireless settings and click “Next”.
• Click Next again and the configuration will be saved.
Page 6 of 8
G. Open the Network Interface
• Check the Wireless USB adapter is installed in which eth by
“ifconfig –a”. In this case, it is installed in eth3.
• The driver will stop all the commands until the network interface assigned to it is opened. You can open the network interface by the following command:
“ifconfig ethX up”. In this case, “ifconfig eth3 up”.
Page 7 of 8
H. Configure the Wireless Settings
• Check the Wireless USB adapter is up by using the command:
“iwconfig”.
• Set the ESSID by using the command:
“iwconfig ethX essid <ESSID>”.
• Set the operation mode of the device by using the command:
“iwconfig ethX mode <mode>”.
where mode:
Managed (Infrastructure Station mode)
Ah-hoc (Ad hoc mode)
• Set the encryption key by using the command:
“iwconfig ethX key open <key>”.
“iwconfig ethX key restricted <key>”.
• Renew the IP by using the command:
“dhcpcd -n ethX”.
Page 8 of 8
```

Any help would be much appreciated.

---

### Post by tshrinivasan on 2007-12-19
What is the device you are working?
any wireless device?

---

### Post by teonghan on 2007-12-21
Rusty023,

i guess you are using aztech usb230wlan, huh? well, i have been trying to install the driver bundled with the installation cd and what i can tell you is that the supplied driver won't work in ubuntu (at least for gusty). i already try to find the alternative driver and found one driver that compatible with it, zd1211rw, that is. but i had trouble installing the driver and detecting the adaptor...sigh. you can refer to [http://ubuntuforums.org/showthread.php?t=35315](http://ubuntuforums.org/showthread.php?t=35315)

---

### Post by pyronaut on 2007-12-21
here's my tuppence...... did u copy the driver to the wireless drivers to /lib/modules?? .. if you didnt then i dont know how the module can be inserted. Of course i dont know the exact location .... on my system running the ipw3945 wireless driver its located at /lib/modules/2.6.22.14-generic/ubuntu/wireless/ipw3945.ko... so i guess thats where your driver module should be located so that when u do the ismod the kernel can load it.. hope this helps.
  cheers

---

### Post by Rusty023 on 2007-12-27
Blah, I don't know...I'm new to Ubuntu, and I tried to follow the instructions but not all of them worked, and the driver wouldn't install. Can someone please guide me through this? Or find a similar driver that works?

---

