---
title: "ubuntu feisty seems no recognize my modem usb arris"
date: 2007-08-03
forum: General Help
---

### Post by jfca283 on 2007-08-03
i have a modem ARRIS TOUCHTONE and i connect to him via USB, it's broadband
well, the problem is this
on dapper it worked very good, even the live CD could run internet
but now don't, here are the ipconfig (from windows) and ubuntu feisty( ifconfig)
searching through the web i found that some modules, CD Ethernet and Usbdnet are not now come in the kernel
so, how can i fix that?
it seems that i must installed some modules
the ipconfig
```

C:\Documents and Settings\Admin\Start Menu>ipconfig/all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : pal
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : Intel(R) PRO/100 VE Network Connecti
on
        Physical Address. . . . . . . . . : 00-10-DC-69-87-EB

Ethernet adapter Local Area Connection 2:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : ARRIS TOUCHSTONE DEVICE
        Physical Address. . . . . . . . . : 00-13-11-E4-A7-A6
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 200.83.14.184
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 200.83.14.1
        DHCP Server . . . . . . . . . . . : 192.168.216.30
        DNS Servers . . . . . . . . . . . : 200.83.1.4
                                            200.74.121.11
                                            200.83.1.5
        Lease Obtained. . . . . . . . . . : Friday, August 03, 2007 4:11:01 PM
        Lease Expires . . . . . . . . . . : Saturday, August 04, 2007 4:11:01 PM


C:\Documents and Settings\Admin\Start Menu>
```

the ifconfig from Feisty, which doesn't have internet
```
juan@juan-desktop:~$ sudo ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:10:DC:69:87:EB  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0:avah Link encap:Ethernet  HWaddr 00:10:DC:69:87:EB  
          inet addr:169.254.9.183  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:806 errors:0 dropped:0 overruns:0 frame:0
          TX packets:806 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:64108 (62.6 KiB)  TX bytes:64108 (62.6 KiB)
```

what is **"eth0:avah"**?
please, any help will be great
i'm now on XP and tired of spyware and all those stuff...
bye

---

### Post by TBerben on 2007-08-04
It could be that the usbdnet modules are provided, but that they're just not loaded at boot. Try running

```
lsmod | grep usbdnet
```

If you get output from this command run:

```
sudo modprobe usbdnet
```

In case this doesn't work, it would be nice to know the model of the modem you're trying to get to work.

---

### Post by jfca283 on 2007-08-04
**lsmod | grep usbdnet** gives me nothing...
i have an ARRIS TOUCHSTONE TM420 and there are 2 PC connected to him via usb...
help me please

---

### Post by jfca283 on 2007-08-05
there is a patch for the kernel?
some modules are not loaded with the kernel, like
cdc_ether, rndis_host y usbnet,
but i'm not sure...

---

