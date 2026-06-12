---
title: "Prolific PL-2303X"
date: 2006-12-21
forum: General Help
---

### Post by mkosmo on 2006-12-21
I am not sure which is a more appropriate forum to place this in, so I am crossposting it here as well as in Laptops/Hardware.  If the moderators do not like me posting this here as well, they can delete it... I just really would like some help if somebody knows how to fix my problem.

Thanks.

> **mkosmo said:**
> I am running Ubuntu Edgy on a Dell E1705.  I have been banging my head on this for a week now, and have finally thrown in the towel and ego to post on the forum. ](*,) 
So, heres my problem.  I got an Airlink101 AC-USBS, which uses a Prolific PL-2303X chip.  I have this connected to a Sun Ultra 2.  I set up minicom at 9800-8-N-1.  I even ran minicom as root to prevent permissions from being the issue.  No traffic seems to be passed.  I know this machine has worked before, since I used minicom with the same settings on my other machine (which had a serial port) when it was here.  Here is a bunch of diagnostics... any ideas?

One thing I notice, is I think its loading the driver for the PL-2303 and not the PL-2303X.  Could this be the problem?  If so, how do I fix it?

Thanks a bunch!


kosmo@blade:~$ dmesg
...
[17282362.036000] usb 3-1: new full speed USB device using uhci_hcd and address 5
[17282362.196000] usb 3-1: configuration #1 chosen from 1 choice
[17282362.196000] pl2303 3-1:1.0: pl2303 converter detected
[17282362.196000] usb 3-1: pl2303 converter now attached to ttyUSB0

kosmo@blade:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 005: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 413c:a005 Dell Computer Corp. 
Bus 001 Device 001: ID 0000:0000  


kosmo@blade:~$ lsusb -v -d 067b:2303

Bus 003 Device 005: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x067b Prolific Technology, Inc.
  idProduct          0x2303 PL2303 Serial Port
  bcdDevice            3.00
  iManufacturer           1 Prolific Technology Inc.
  iProduct                2 USB-Serial Controller
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x000a  1x 10 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)

kosmo@blade:~$ cat /proc/bus/usb/devices 
...
T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  5 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=067b ProdID=2303 Rev= 3.00
S:  Manufacturer=Prolific Technology Inc.
S:  Product=USB-Serial Controller
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=00 Prot=00 Driver=pl2303
E:  Ad=81(I) Atr=03(Int.) MxPS=  10 Ivl=1ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
...

---

### Post by ubmac on 2006-12-31
Hi,
I installed ubuntu to use a tool not included in windows, and linux is much better the last time I installed linux.
I'm trying to work with a PL-2303X serial adaptar too, and came to this thread.
Found this link [http://koti.mbnet.fi/lonnberg/pl2303x.html](http://koti.mbnet.fi/lonnberg/pl2303x.html) ,
but my problem was not to link to /dev/ttyS0 with the command **ln -b /dev/ttyUSB0 /dev/ttyS0** :D > The following patch modifies the driver for the Prolific PL-2303 USB-serial adapter to add support for the highly similar but incompatible PL-2303X adapter. The PL-2303X has the same vendor ID and product ID as the older PL-2303, which means that it will be incorrectly detected as a PL-2303 by the driver currently in the Linux kernel. Attempting to use a PL-2303X as a PL-2303 simply results in an inability to transfer data through the serial port. In other words, nothing happens. This patch autodetects whether a PL-2303 or a PL-2303X is used and changes the initialisation sequence accordingly.

The PL-2303X can be distinguished from a PL-2303 by checking bMaxPacketSize0 for the device using lsusb -v -d 067b:2303 (as root). If bMaxPacketSize0 is 64, you probably have a PL-2303X and need this patch.> The main kernel tree includes PL-2303X support starting from 2.6.8 (I can confirm that PL-2303X works on 2.6.11rc2 without my patch), making this patch unnecessary.

Happy new year.

---

