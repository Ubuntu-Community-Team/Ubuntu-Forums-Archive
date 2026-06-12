---
title: "USB Missile Launcher - Help!"
date: 2006-12-25
forum: General Help
---

### Post by oolunchbox on 2006-12-25
I asked for the [USB Missile Launcher]("http://www.thinkgeek.com/geektoys/cubegoodies/86b8/") from ThinkGeek.com for Christmas knowing that it was windows/mac only hoping I could get the software to run in wine. The software installs and runs perfectly but I cannot seem to get it to actually work. Is there someting I need to do to make wine know which USB port the millisle launcher is on?

Thanks,
Chris

p.s.
dmesg reads:
```
[18679785.412000] usb 1-5: configuration #1 chosen from 1 choice
[18679785.428000] input: Tenx Nonstandard Devic as /class/input/input6
[18679785.428000] input: USB HID v1.10 Device [Tenx Nonstandard Devic] on usb-0000:00:02.0-5
[18679785.440000] input: Tenx Nonstandard Devic as /class/input/input7
[18679785.440000] input: USB HID v1.10 Device [Tenx Nonstandard Devic] on usb-0000:00:02.0-5

```
There is a TenxHID.dll file in the program folder, is there a way to make wine know to use that dll?

---

### Post by cilynx on 2006-12-27
google: "usb missile launcher" ubuntu

you'll get a bunch of responses you'll like.  You don't need wine.

---

### Post by oolunchbox on 2006-12-28
spectacular. thanks a bunch. this thing is a ton of fun and i'd reccommend it as a gift to yourself or anyone really!

---

### Post by usien on 2006-12-28
wat exactly is a USB missile launcher?is it a weapon of mass destruction? :twisted:

---

### Post by majoridiot on 2006-12-28
a weapon of mass *distraction*...

---

### Post by leftcase on 2007-01-02
I received a usb missile launcher for Christmas! Great fun.

I've written a simple php/perl web script that allows you to remote control your usb missile launcher through the web. It interfaces with the [_script written by Scott Weston here_]("http://scott.weston.id.au/software/pymissile/") to unleash remote destruction!

The [_web interface to usb missile launcher is available for anyone to use here_]("http://www.justuber.com/blog/2007/01/01/usb-missile-launcher-web-control-interface-for-linux"). If it's of any use to you, I hope you enjoy it.

---

### Post by patwack on 2007-01-27
i've just got one of these and can't get it to work

it fails at the "sudo python setup.py install" stage, this is the output i get

```
running install
running build
running build_ext
building 'usb' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.4 -c pyusb.c -o build/temp.linux-i686-2.4/pyusb.o
In file included from pyusb.c:12:
pyusb.h:4:20: error: Python.h: No such file or directory
pyusb.h:5:26: error: structmember.h: No such file or directory
In file included from pyusb.c:12:
pyusb.h:46: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
pyusb.h:59: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
pyusb.h:73: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
pyusb.h:87: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
pyusb.h:108: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
pyusb.h:118: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
pyusb.h:154: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.h:172: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.h:178: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.h:183: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.h:188: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.h:193: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.h:198: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.h:203: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.h:208: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.h:213: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.h:218: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.h:223: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.h:228: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.h:233: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.h:238: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.h:247: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.c:30: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.c:69: error: expected ‘)’ before ‘*’ token
pyusb.c:89: error: expected ‘)’ before ‘*’ token
pyusb.c:124: error: expected ‘)’ before ‘*’ token
pyusb.c:181: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.c:204: error: expected ‘)’ before ‘*’ token
pyusb.c:222: error: expected ‘)’ before ‘*’ token
pyusb.c:295: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Py_usb_Endpoint_Members’
pyusb.c:331: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Py_usb_Endpoint_Methods’
pyusb.c:335: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Py_usb_Endpoint_Type’
pyusb.c: In function ‘set_Endpoint_fields’:
pyusb.c:390: error: ‘Py_usb_Endpoint’ has no member named ‘address’
pyusb.c:391: error: ‘Py_usb_Endpoint’ has no member named ‘type’
pyusb.c:392: error: ‘Py_usb_Endpoint’ has no member named ‘maxPacketSize’
pyusb.c:393: error: ‘Py_usb_Endpoint’ has no member named ‘interval’
pyusb.c:394: error: ‘Py_usb_Endpoint’ has no member named ‘refresh’
pyusb.c: In function ‘new_Endpoint’:
pyusb.c:404: warning: implicit declaration of function ‘PyObject_New’
pyusb.c:404: error: expected expression before ‘Py_usb_Endpoint’
pyusb.c:405: warning: assignment makes pointer from integer without a cast
pyusb.c: At top level:
pyusb.c:413: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Py_usb_Interface_Members’
pyusb.c:457: error: expected ‘)’ before ‘*’ token
pyusb.c:463: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Py_usb_Interface_Methods’
pyusb.c:467: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Py_usb_Interface_Type’
pyusb.c: In function ‘set_Interface_fields’:
pyusb.c:524: error: ‘Py_usb_Interface’ has no member named ‘interfaceNumber’
pyusb.c:525: error: ‘Py_usb_Interface’ has no member named ‘alternateSetting’
pyusb.c:526: error: ‘Py_usb_Interface’ has no member named ‘interfaceClass’
pyusb.c:527: error: ‘Py_usb_Interface’ has no member named ‘interfaceSubClass’
pyusb.c:528: error: ‘Py_usb_Interface’ has no member named ‘interfaceProtocol’
pyusb.c:529: error: ‘Py_usb_Interface’ has no member named ‘iInterface’
pyusb.c:531: error: ‘Py_usb_Interface’ has no member named ‘endpoints’
pyusb.c:531: warning: implicit declaration of function ‘PyTuple_New’
pyusb.c:533: error: ‘Py_usb_Interface’ has no member named ‘endpoints’
pyusb.c:538: warning: implicit declaration of function ‘PyTuple_SET_ITEM’
pyusb.c:538: error: ‘Py_usb_Interface’ has no member named ‘endpoints’
pyusb.c:539: error: ‘PyObject’ undeclared (first use in this function)
pyusb.c:539: error: (Each undeclared identifier is reported only once
pyusb.c:539: error: for each function it appears in.)
pyusb.c:539: error: expected expression before ‘)’ token
pyusb.c: In function ‘new_Interface’:
pyusb.c:548: warning: implicit declaration of function ‘PyObject_NEW’
pyusb.c:548: error: expected expression before ‘Py_usb_Interface’
pyusb.c:548: warning: assignment makes pointer from integer without a cast
pyusb.c:553: warning: implicit declaration of function ‘PyErr_Occurred’
pyusb.c:554: warning: implicit declaration of function ‘Py_XDECREF’
pyusb.c:554: error: ‘PyObject’ undeclared (first use in this function)
pyusb.c:554: error: expected expression before ‘)’ token
pyusb.c: At top level:
pyusb.c:562: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Py_usb_Configuration_Members’
pyusb.c:614: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Py_usb_Configuration_Methods’
pyusb.c:619: error: expected ‘)’ before ‘*’ token
pyusb.c:625: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Py_usb_Configuration_Type’
pyusb.c: In function ‘set_Configuration_fields’:
pyusb.c:681: error: ‘PyObject’ undeclared (first use in this function)
pyusb.c:681: error: ‘t1’ undeclared (first use in this function)
pyusb.c:683: error: ‘Py_usb_Configuration’ has no member named ‘totalLength’
pyusb.c:684: error: ‘Py_usb_Configuration’ has no member named ‘value’
pyusb.c:685: error: ‘Py_usb_Configuration’ has no member named ‘iConfiguration’
pyusb.c:686: error: ‘Py_usb_Configuration’ has no member named ‘selfPowered’
pyusb.c:687: error: ‘Py_usb_Configuration’ has no member named ‘remoteWakeup’
pyusb.c:688: error: ‘Py_usb_Configuration’ has no member named ‘maxPower’
pyusb.c:690: error: ‘Py_usb_Configuration’ has no member named ‘interfaces’
pyusb.c:692: error: ‘Py_usb_Configuration’ has no member named ‘interfaces’
pyusb.c:702: error: expected expression before ‘)’ token
pyusb.c:704: error: ‘Py_usb_Configuration’ has no member named ‘interfaces’
pyusb.c: In function ‘new_Configuration’:
pyusb.c:714: error: expected expression before ‘Py_usb_Configuration’
pyusb.c:714: warning: assignment makes pointer from integer without a cast
pyusb.c:720: warning: implicit declaration of function ‘Py_DECREF’
pyusb.c:720: error: ‘PyObject’ undeclared (first use in this function)
pyusb.c:720: error: expected expression before ‘)’ token
pyusb.c: At top level:
pyusb.c:728: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Py_usb_Device_Members’
pyusb.c:817: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.c:825: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Py_usb_Device_Methods’
pyusb.c:837: error: expected ‘)’ before ‘*’ token
pyusb.c:843: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Py_usb_Device_Type’
pyusb.c: In function ‘set_Device_fields’:
pyusb.c:901: error: ‘Py_usb_Device’ has no member named ‘usbVersion’
pyusb.c:902: error: ‘Py_usb_Device’ has no member named ‘usbVersion’
pyusb.c:903: error: ‘Py_usb_Device’ has no member named ‘usbVersion’
pyusb.c:904: error: ‘Py_usb_Device’ has no member named ‘usbVersion’
pyusb.c:905: error: ‘Py_usb_Device’ has no member named ‘usbVersion’
pyusb.c:906: error: ‘Py_usb_Device’ has no member named ‘usbVersion’
pyusb.c:908: error: ‘Py_usb_Device’ has no member named ‘deviceVersion’
pyusb.c:909: error: ‘Py_usb_Device’ has no member named ‘deviceVersion’
pyusb.c:910: error: ‘Py_usb_Device’ has no member named ‘deviceVersion’
pyusb.c:911: error: ‘Py_usb_Device’ has no member named ‘deviceVersion’
pyusb.c:912: error: ‘Py_usb_Device’ has no member named ‘deviceVersion’
pyusb.c:913: error: ‘Py_usb_Device’ has no member named ‘deviceVersion’
pyusb.c:915: error: ‘Py_usb_Device’ has no member named ‘deviceClass’
pyusb.c:916: error: ‘Py_usb_Device’ has no member named ‘deviceSubClass’
pyusb.c:917: error: ‘Py_usb_Device’ has no member named ‘deviceProtocol’
pyusb.c:918: error: ‘Py_usb_Device’ has no member named ‘maxPacketSize’
pyusb.c:919: error: ‘Py_usb_Device’ has no member named ‘idVendor’
pyusb.c:920: error: ‘Py_usb_Device’ has no member named ‘idProduct’
pyusb.c:921: error: ‘Py_usb_Device’ has no member named ‘iManufacturer’
pyusb.c:922: error: ‘Py_usb_Device’ has no member named ‘iProduct’
pyusb.c:923: error: ‘Py_usb_Device’ has no member named ‘iSerialNumber’
pyusb.c:924: warning: implicit declaration of function ‘strcpy’
pyusb.c:924: warning: incompatible implicit declaration of built-in function ‘strcpy’
pyusb.c:924: error: ‘Py_usb_Device’ has no member named ‘filename’
pyusb.c:925: error: ‘Py_usb_Device’ has no member named ‘dev’
pyusb.c:927: error: ‘Py_usb_Device’ has no member named ‘configurations’
pyusb.c:929: error: ‘Py_usb_Device’ has no member named ‘configurations’
pyusb.c:932: error: ‘Py_usb_Device’ has no member named ‘configurations’
pyusb.c:932: error: ‘PyObject’ undeclared (first use in this function)
pyusb.c:932: error: expected expression before ‘)’ token
pyusb.c: In function ‘new_Device’:
pyusb.c:941: error: expected expression before ‘Py_usb_Device’
pyusb.c:941: warning: assignment makes pointer from integer without a cast
pyusb.c:947: error: ‘PyObject’ undeclared (first use in this function)
pyusb.c:947: error: expected expression before ‘)’ token
pyusb.c: At top level:
pyusb.c:955: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Py_usb_Bus_Members’
pyusb.c:977: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Py_usb_Bus_Methods’
pyusb.c:982: error: expected ‘)’ before ‘*’ token
pyusb.c:988: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Py_usb_Bus_Type’
pyusb.c: In function ‘new_Bus’:
pyusb.c:1046: error: expected expression before ‘Py_usb_Bus’
pyusb.c:1046: warning: assignment makes pointer from integer without a cast
pyusb.c:1049: error: ‘Py_usb_Bus’ has no member named ‘location’
pyusb.c:1050: warning: incompatible implicit declaration of built-in function ‘strcpy’
pyusb.c:1050: error: ‘Py_usb_Bus’ has no member named ‘dirname’
pyusb.c:1052: error: ‘Py_usb_Bus’ has no member named ‘devices’
pyusb.c:1054: error: ‘Py_usb_Bus’ has no member named ‘devices’
pyusb.c:1055: error: ‘PyObject’ undeclared (first use in this function)
pyusb.c:1055: error: expected expression before ‘)’ token
pyusb.c:1060: error: ‘Py_usb_Bus’ has no member named ‘devices’
pyusb.c:1060: error: expected expression before ‘)’ token
pyusb.c:1063: error: expected expression before ‘)’ token
pyusb.c: At top level:
pyusb.c:1071: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Py_usb_DeviceHandle_Members’
pyusb.c:1078: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.c:1181: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.c:1214: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.c:1250: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.c:1272: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.c:1306: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.c:1357: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.c:1407: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.c:1458: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.c:1508: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.c:1536: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.c:1549: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.c:1580: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.c:1637: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.c:1693: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Py_usb_DeviceHandle_Methods’
pyusb.c:1839: error: expected ‘)’ before ‘*’ token
pyusb.c:1855: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Py_usb_DeviceHandle_Type’
pyusb.c: In function ‘new_DeviceHandle’:
pyusb.c:1912: error: expected expression before ‘Py_usb_DeviceHandle’
pyusb.c:1912: warning: assignment makes pointer from integer without a cast
pyusb.c:1915: error: ‘Py_usb_Device’ has no member named ‘dev’
pyusb.c:1918: warning: implicit declaration of function ‘PyErr_SetString’
pyusb.c:1918: error: ‘PyExc_USBError’ undeclared (first use in this function)
pyusb.c:1919: error: ‘PyObject’ undeclared (first use in this function)
pyusb.c:1919: error: expected expression before ‘)’ token
pyusb.c:1923: error: ‘Py_usb_DeviceHandle’ has no member named ‘deviceHandle’
pyusb.c:1924: error: ‘Py_usb_DeviceHandle’ has no member named ‘interfaceClaimed’
pyusb.c: At top level:
pyusb.c:1934: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pyusb.c:1975: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘usb_Methods’
pyusb.c: In function ‘initusb’:
pyusb.c:1989: error: ‘PyObject’ undeclared (first use in this function)
pyusb.c:1989: error: ‘module’ undeclared (first use in this function)
pyusb.c:1991: error: ‘PyExc_USBError’ undeclared (first use in this function)
pyusb.c:1991: warning: implicit declaration of function ‘PyErr_NewException’
pyusb.c:1991: error: ‘PyExc_IOError’ undeclared (first use in this function)
pyusb.c:1994: warning: implicit declaration of function ‘Py_InitModule3’
pyusb.c:1994: error: ‘usb_Methods’ undeclared (first use in this function)
pyusb.c:1997: warning: implicit declaration of function ‘PyType_Ready’
pyusb.c:1997: error: ‘Py_usb_Endpoint_Type’ undeclared (first use in this function)
pyusb.c:1998: warning: implicit declaration of function ‘Py_INCREF’
pyusb.c:1999: warning: implicit declaration of function ‘PyModule_AddObject’
pyusb.c:1999: error: expected expression before ‘)’ token
pyusb.c:2001: error: ‘Py_usb_Interface_Type’ undeclared (first use in this function)
pyusb.c:2003: error: expected expression before ‘)’ token
pyusb.c:2005: error: ‘Py_usb_Configuration_Type’ undeclared (first use in this function)
pyusb.c:2007: error: expected expression before ‘)’ token
pyusb.c:2009: error: ‘Py_usb_Device_Type’ undeclared (first use in this function)
pyusb.c:2011: error: expected expression before ‘)’ token
pyusb.c:2013: error: ‘Py_usb_Bus_Type’ undeclared (first use in this function)
pyusb.c:2015: error: expected expression before ‘)’ token
pyusb.c:2017: error: ‘Py_usb_DeviceHandle_Type’ undeclared (first use in this function)
pyusb.c:2019: error: expected expression before ‘)’ token
pyusb.c:2021: warning: implicit declaration of function ‘installModuleConstants’
error: command 'gcc' failed with exit status 1

```

i have no idea what i'm doing wrong, i followed the instructions on scotts page exactly... hmmm

---

### Post by phossal on 2007-01-27
I had never heard of this, and I visit ThinkGeek occasionally. It's stupid. I'm going to get one. ;)

---

### Post by cilynx on 2007-01-27
```

sudo apt-get install python-dev

```
You need the development setup for python as you're compiling the program...

---

