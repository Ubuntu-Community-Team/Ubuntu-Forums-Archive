---
title: "Installing Redhat driver on Ubuntu?"
date: 2007-12-19
forum: General Help
---

### Post by skychris on 2007-12-19
Hello,

I have an USB to Serial adapter and I'm struggling to get it work on my laptop. It uses a Prolific pl2303 chip and the only recent driver I found is intended for redhat (7.3, 8 and 9)
it doesn't come as a RPM file so I guess I can't use "alien", It comes as source files, a "Makefile" and a "pl2303.c". 
I tried to use the function "make" but with no luck as it gives me a bunch of errors. 
Is there another way to use Redhat intended install files to  work on Ubuntu?

the files can be found here,
[HTML]http://www.prolific.com.tw/eng/downloads.asp?ID=31[/HTML]

thanks

Chris:)

---

### Post by Sef on 2007-12-19
1) Did you install build-essential?

If not, then open the terminal and type in these codes:

```
sudo apt-get update
```

```
sudo apt-get install build-essential
```

Have your cd that used for install handy.   It will use that for the install.

2) What errors are you getting?

---

### Post by skychris on 2007-12-19
Thanks for your quick answer:)

I updated my "essential-build" and tried to compile again but no luck. there is so many errors and warnings that it would be too long to list....
here's the "Makefile" for the driver, it looks like it has references to a other kernel that I have (linux-2.4) and I have gutsy on my machine.
```
# USB-Serial Makefile

#

# USAGE:

# To install driver -

#        make inst (The Makefile will check the module and compile and link it automatically. It will also remove

#                   the loaded USB-Serial driver)

#

# To uninstall driver -

#        make uninst

#

# To uninstall all drivers (including base driver) -

#        make uninst_all

#

# To remove module (*.o) files -

#        make clean

#



KINCLUDES=/usr/src/linux-2.4/include

DRVINCLUDES=/usr/src/linux-2.4/drivers/usb/serial



# uncomment line below if you have SMP

#SMPFLAGS=	-D__SMP__ -DCONFIG_SMP=1



# Unless you have a 386/486, you shouldn't need

# to change anything below here...



# CPUFLAGS=	-DCPU=586 -march=i586

MODULE=		pl2303

BASE_MODULE=	usbserial

CC=		gcc

CPPFLAGS=	-D__KERNEL__ -I$(KINCLUDES) -I$(DRVINCLUDES)

MODFLAGS=	-DMODULE

KERNFLAGS=      $(CPPFLAGS) $(CPUFLAGS) $(SMPFLAGS) \

		-Wall -Wstrict-prototypes -Wno-trigraphs -O2 -fomit-frame-pointer \

		-fno-strict-aliasing -fno-common -Wno-unused

# EXTRA_CFLAGS=	-DEXPORT_SYMTAB

# DBGCFLAGS=	-DDEBUG -DCONFIG_USB_SERIAL_DEBUG

CFLAGS=		$(KERNFLAGS) $(DBGCFLAGS) $(MODFLAGS)



RELVER=		$(shell uname -r)



all::		$(MODULE).o



$(MODULE).o:	$(MODULE).c

	$(CC) $(CFLAGS) -c $<



.PHONY: inst, uninst, uninst_all, clean



inst:	$(MODULE).o

ifneq (,$(findstring $(MODULE),$(shell lsmod | grep $(MODULE))))		# if module was already loaded

	rmmod $(MODULE)

	insmod ./$(MODULE).o

else

ifeq (,$(findstring $(BASE_MODULE),$(shell lsmod | grep $(BASE_MODULE))))	# if there is no base module

	insmod /lib/modules/$(RELVER)/kernel/drivers/usb/serial/$(BASE_MODULE).o

endif	

	insmod ./$(MODULE).o

endif

	@echo

	@echo ">> Please unplug and plug the cable if it is already plugged-in. <<"

	@echo



uninst:

ifneq (,$(findstring $(MODULE),$(shell lsmod | grep $(MODULE))))		# if module was loaded

	rmmod $(MODULE)

endif	

	@echo

	@echo ">> The USB-Serial driver is removed! <<"

	@echo



uninst_all:

ifneq (,$(findstring $(MODULE),$(shell lsmod | grep $(MODULE))))		# if module was loaded

	rmmod $(MODULE)

endif

ifneq (,$(findstring $(BASE_MODULE),$(shell lsmod | grep $(BASE_MODULE))))	# if base module was loaded

	rmmod $(BASE_MODULE)

endif	

	@echo

	@echo ">> The USB-Serial and base driver are removed! <<"

	@echo



clean:

	rm -f *.o

```

I saw a tutorial saying me that I could change some lines within the "Makefile" to get it work... would it work?

Cheers

---

### Post by skychris on 2007-12-19
Following my last post, here's the list of errors I get trying to compile 
```
chris@laptop:~/Documents/Softs/UsbtoSerial/Disk/Redhat9$ sudo make all
gcc -D__KERNEL__ -I/usr/src/linux-2.4/include -I/usr/src/linux-2.4/drivers/usb/serial   -Wall -Wstrict-prototypes -Wno-trigraphs -O2 -fomit-frame-pointer -fno-strict-aliasing -fno-common -Wno-unused  -DMODULE -c pl2303.c
pl2303.c:33:26: error: linux/config.h: No such file or directory
pl2303.c:36:24: error: linux/init.h: No such file or directory
pl2303.c:37:24: error: linux/slab.h: No such file or directory
pl2303.c:39:30: error: linux/tty_driver.h: No such file or directory
pl2303.c:40:28: error: linux/tty_flip.h: No such file or directory
pl2303.c:42:26: error: linux/module.h: No such file or directory
pl2303.c:43:28: error: linux/spinlock.h: No such file or directory
pl2303.c:44:25: error: asm/uaccess.h: No such file or directory
pl2303.c:45:23: error: linux/usb.h: No such file or directory
pl2303.c:53:24: error: usb-serial.h: No such file or directory
pl2303.c:54:20: error: pl2303.h: No such file or directory
pl2303.c:64: error: array type has incomplete element type
pl2303.c:65: warning: implicit declaration of function ‘USB_DEVICE’
pl2303.c:65: error: ‘PL2303_VENDOR_ID’ undeclared here (not in a function)
pl2303.c:65: error: ‘PL2303_PRODUCT_ID’ undeclared here (not in a function)
pl2303.c:66: error: ‘PL2303_PRODUCT_ID_RSAQ2’ undeclared here (not in a function)
pl2303.c:67: error: ‘IODATA_VENDOR_ID’ undeclared here (not in a function)
pl2303.c:67: error: ‘IODATA_PRODUCT_ID’ undeclared here (not in a function)
pl2303.c:68: error: ‘ATEN_VENDOR_ID’ undeclared here (not in a function)
pl2303.c:68: error: ‘ATEN_PRODUCT_ID’ undeclared here (not in a function)
pl2303.c:69: error: ‘ELCOM_VENDOR_ID’ undeclared here (not in a function)
pl2303.c:69: error: ‘ELCOM_PRODUCT_ID’ undeclared here (not in a function)
pl2303.c:70: error: ‘ITEGNO_VENDOR_ID’ undeclared here (not in a function)
pl2303.c:70: error: ‘ITEGNO_PRODUCT_ID’ undeclared here (not in a function)
pl2303.c:71: error: ‘MA620_VENDOR_ID’ undeclared here (not in a function)
pl2303.c:71: error: ‘MA620_PRODUCT_ID’ undeclared here (not in a function)
pl2303.c:72: error: ‘RATOC_VENDOR_ID’ undeclared here (not in a function)
pl2303.c:72: error: ‘RATOC_PRODUCT_ID’ undeclared here (not in a function)
pl2303.c:76: warning: data definition has no type or storage class
pl2303.c:76: warning: type defaults to ‘int’ in declaration of ‘MODULE_DEVICE_TABLE’
pl2303.c:76: warning: parameter names (without types) in function declaration
pl2303.c:102: warning: ‘struct file’ declared inside parameter list
pl2303.c:102: warning: its scope is only this definition or declaration, which is probably not what you want
pl2303.c:102: warning: ‘struct usb_serial_port’ declared inside parameter list
pl2303.c:103: warning: ‘struct file’ declared inside parameter list
pl2303.c:103: warning: ‘struct usb_serial_port’ declared inside parameter list
pl2303.c:105: warning: ‘struct termios’ declared inside parameter list
pl2303.c:105: warning: ‘struct usb_serial_port’ declared inside parameter list
pl2303.c:107: warning: ‘struct file’ declared inside parameter list
pl2303.c:107: warning: ‘struct usb_serial_port’ declared inside parameter list
pl2303.c:108: warning: ‘struct urb’ declared inside parameter list
pl2303.c:109: warning: ‘struct urb’ declared inside parameter list
pl2303.c:110: warning: ‘struct urb’ declared inside parameter list
pl2303.c:112: warning: ‘struct usb_serial_port’ declared inside parameter list
pl2303.c:113: warning: ‘struct usb_serial_port’ declared inside parameter list
pl2303.c:114: warning: ‘struct usb_serial’ declared inside parameter list
pl2303.c:115: warning: ‘struct usb_serial’ declared inside parameter list
pl2303.c:119: error: variable ‘pl2303_device’ has initializer but incomplete type
pl2303.c:120: error: unknown field ‘owner’ specified in initializer
pl2303.c:120: error: ‘THIS_MODULE’ undeclared here (not in a function)
pl2303.c:120: warning: excess elements in struct initializer
pl2303.c:120: warning: (near initialization for ‘pl2303_device’)
pl2303.c:121: error: unknown field ‘name’ specified in initializer
pl2303.c:121: warning: excess elements in struct initializer
pl2303.c:121: warning: (near initialization for ‘pl2303_device’)
pl2303.c:122: error: unknown field ‘id_table’ specified in initializer
pl2303.c:122: warning: excess elements in struct initializer
pl2303.c:122: warning: (near initialization for ‘pl2303_device’)
pl2303.c:123: error: unknown field ‘num_interrupt_in’ specified in initializer
pl2303.c:123: error: ‘NUM_DONT_CARE’ undeclared here (not in a function)
pl2303.c:123: warning: excess elements in struct initializer
pl2303.c:123: warning: (near initialization for ‘pl2303_device’)
pl2303.c:124: error: unknown field ‘num_bulk_in’ specified in initializer
pl2303.c:124: warning: excess elements in struct initializer
pl2303.c:124: warning: (near initialization for ‘pl2303_device’)
pl2303.c:125: error: unknown field ‘num_bulk_out’ specified in initializer
pl2303.c:125: warning: excess elements in struct initializer
pl2303.c:125: warning: (near initialization for ‘pl2303_device’)
pl2303.c:126: error: unknown field ‘num_ports’ specified in initializer
pl2303.c:126: warning: excess elements in struct initializer
pl2303.c:126: warning: (near initialization for ‘pl2303_device’)
pl2303.c:127: error: unknown field ‘open’ specified in initializer
pl2303.c:127: warning: excess elements in struct initializer
pl2303.c:127: warning: (near initialization for ‘pl2303_device’)
pl2303.c:128: error: unknown field ‘close’ specified in initializer
pl2303.c:128: warning: excess elements in struct initializer
pl2303.c:128: warning: (near initialization for ‘pl2303_device’)
pl2303.c:129: error: unknown field ‘write’ specified in initializer
pl2303.c:129: warning: excess elements in struct initializer
pl2303.c:129: warning: (near initialization for ‘pl2303_device’)
pl2303.c:130: error: unknown field ‘ioctl’ specified in initializer
pl2303.c:130: warning: excess elements in struct initializer
pl2303.c:130: warning: (near initialization for ‘pl2303_device’)
pl2303.c:131: error: unknown field ‘break_ctl’ specified in initializer
pl2303.c:131: warning: excess elements in struct initializer
pl2303.c:131: warning: (near initialization for ‘pl2303_device’)
pl2303.c:132: error: unknown field ‘set_termios’ specified in initializer
pl2303.c:132: warning: excess elements in struct initializer
pl2303.c:132: warning: (near initialization for ‘pl2303_device’)
pl2303.c:133: error: unknown field ‘read_bulk_callback’ specified in initializer
pl2303.c:133: warning: excess elements in struct initializer
pl2303.c:133: warning: (near initialization for ‘pl2303_device’)
pl2303.c:134: error: unknown field ‘read_int_callback’ specified in initializer
pl2303.c:134: warning: excess elements in struct initializer
pl2303.c:134: warning: (near initialization for ‘pl2303_device’)
pl2303.c:135: error: unknown field ‘write_bulk_callback’ specified in initializer
pl2303.c:135: warning: excess elements in struct initializer
pl2303.c:135: warning: (near initialization for ‘pl2303_device’)
pl2303.c:136: error: unknown field ‘startup’ specified in initializer
pl2303.c:136: warning: excess elements in struct initializer
pl2303.c:136: warning: (near initialization for ‘pl2303_device’)
pl2303.c:137: error: unknown field ‘shutdown’ specified in initializer
pl2303.c:137: warning: excess elements in struct initializer
pl2303.c:137: warning: (near initialization for ‘pl2303_device’)
pl2303.c:141: error: expected specifier-qualifier-list before ‘u8’
pl2303.c:147: warning: ‘struct usb_serial’ declared inside parameter list
pl2303.c:148: error: conflicting types for ‘pl2303_startup’
pl2303.c:114: error: previous declaration of ‘pl2303_startup’ was here
pl2303.c: In function ‘pl2303_startup’:
pl2303.c:152: error: dereferencing pointer to incomplete type
pl2303.c:153: warning: implicit declaration of function ‘kmalloc’
pl2303.c:153: error: ‘GFP_KERNEL’ undeclared (first use in this function)
pl2303.c:153: error: (Each undeclared identifier is reported only once
pl2303.c:153: error: for each function it appears in.)
pl2303.c:153: warning: assignment makes pointer from integer without a cast
pl2303.c:156: warning: implicit declaration of function ‘memset’
pl2303.c:156: warning: incompatible implicit declaration of built-in function ‘memset’
pl2303.c:157: error: dereferencing pointer to incomplete type
pl2303.c: At top level:
pl2303.c:162: error: expected declaration specifiers or ‘...’ before ‘u8’
pl2303.c:162: warning: ‘struct usb_device’ declared inside parameter list
pl2303.c: In function ‘set_control_lines’:
pl2303.c:166: warning: implicit declaration of function ‘usb_control_msg’
pl2303.c:166: warning: implicit declaration of function ‘usb_sndctrlpipe’
pl2303.c:168: error: ‘value’ undeclared (first use in this function)
pl2303.c:168: error: ‘NULL’ undeclared (first use in this function)
pl2303.c:169: warning: implicit declaration of function ‘dbg’
pl2303.c: At top level:
pl2303.c:173: warning: ‘struct usb_serial_port’ declared inside parameter list
pl2303.c:174: error: conflicting types for ‘pl2303_write’
pl2303.c:112: error: previous declaration of ‘pl2303_write’ was here
pl2303.c: In function ‘pl2303_write’:
pl2303.c:177: error: dereferencing pointer to incomplete type
pl2303.c:179: error: dereferencing pointer to incomplete type
pl2303.c:184: error: dereferencing pointer to incomplete type
pl2303.c:184: error: dereferencing pointer to incomplete type
pl2303.c:186: warning: implicit declaration of function ‘copy_from_user’
pl2303.c:186: error: dereferencing pointer to incomplete type
pl2303.c:189: warning: implicit declaration of function ‘memcpy’
pl2303.c:189: warning: incompatible implicit declaration of built-in function ‘memcpy’
pl2303.c:189: error: dereferencing pointer to incomplete type
pl2303.c:192: warning: implicit declaration of function ‘usb_serial_debug_data’
pl2303.c:192: error: dereferencing pointer to incomplete type
pl2303.c:194: error: dereferencing pointer to incomplete type
pl2303.c:195: error: dereferencing pointer to incomplete type
pl2303.c:195: error: dereferencing pointer to incomplete type
pl2303.c:196: warning: implicit declaration of function ‘usb_submit_urb’
pl2303.c:196: error: dereferencing pointer to incomplete type
pl2303.c:198: warning: implicit declaration of function ‘err’
pl2303.c: At top level:
pl2303.c:207: warning: ‘struct termios’ declared inside parameter list
pl2303.c:207: warning: ‘struct usb_serial_port’ declared inside parameter list
pl2303.c:208: error: conflicting types for ‘pl2303_set_termios’
pl2303.c:105: error: previous declaration of ‘pl2303_set_termios’ was here
pl2303.c: In function ‘pl2303_set_termios’:
pl2303.c:209: error: dereferencing pointer to incomplete type
pl2303.c:210: error: dereferencing pointer to incomplete type
pl2303.c:216: error: dereferencing pointer to incomplete type
pl2303.c:217: error: dereferencing pointer to incomplete type
pl2303.c:219: error: dereferencing pointer to incomplete type
pl2303.c:219: error: dereferencing pointer to incomplete type
pl2303.c:224: error: dereferencing pointer to incomplete type
pl2303.c:225: error: dereferencing pointer to incomplete type
pl2303.c:225: error: ‘tty_std_termios’ undeclared (first use in this function)
pl2303.c:226: error: dereferencing pointer to incomplete type
pl2303.c:226: error: ‘B9600’ undeclared (first use in this function)
pl2303.c:226: error: ‘CS8’ undeclared (first use in this function)
pl2303.c:226: error: ‘CREAD’ undeclared (first use in this function)
pl2303.c:226: error: ‘HUPCL’ undeclared (first use in this function)
pl2303.c:226: error: ‘CLOCAL’ undeclared (first use in this function)
pl2303.c:227: error: dereferencing pointer to incomplete type
pl2303.c:229: error: dereferencing pointer to incomplete type
pl2303.c:232: error: dereferencing pointer to incomplete type
pl2303.c:233: warning: implicit declaration of function ‘RELEVANT_IFLAG’
pl2303.c:233: error: dereferencing pointer to incomplete type
pl2303.c:233: error: dereferencing pointer to incomplete type
pl2303.c:239: error: ‘GFP_KERNEL’ undeclared (first use in this function)
pl2303.c:239: warning: assignment makes pointer from integer without a cast
pl2303.c:244: warning: incompatible implicit declaration of built-in function ‘memset’
pl2303.c:246: error: dereferencing pointer to incomplete type
pl2303.c:246: warning: implicit declaration of function ‘usb_rcvctrlpipe’
pl2303.c:246: error: dereferencing pointer to incomplete type
pl2303.c:253: error: dereferencing pointer to incomplete type
pl2303.c:253: error: dereferencing pointer to incomplete type
pl2303.c:255: error: ‘NULL’ undeclared (first use in this function)
pl2303.c:259: error: ‘CSIZE’ undeclared (first use in this function)
pl2303.c:261: error: ‘CS5’ undeclared (first use in this function)
pl2303.c:262: error: ‘CS6’ undeclared (first use in this function)
pl2303.c:263: error: ‘CS7’ undeclared (first use in this function)
pl2303.c:271: error: ‘CBAUD’ undeclared (first use in this function)
pl2303.c:272: error: ‘B0’ undeclared (first use in this function)
pl2303.c:273: error: ‘B75’ undeclared (first use in this function)
pl2303.c:274: error: ‘B150’ undeclared (first use in this function)
pl2303.c:275: error: ‘B300’ undeclared (first use in this function)
pl2303.c:276: error: ‘B600’ undeclared (first use in this function)
pl2303.c:277: error: ‘B1200’ undeclared (first use in this function)
pl2303.c:278: error: ‘B1800’ undeclared (first use in this function)
pl2303.c:279: error: ‘B2400’ undeclared (first use in this function)
pl2303.c:280: error: ‘B4800’ undeclared (first use in this function)
pl2303.c:282: error: ‘B19200’ undeclared (first use in this function)
pl2303.c:283: error: ‘B38400’ undeclared (first use in this function)
pl2303.c:284: error: ‘B57600’ undeclared (first use in this function)
pl2303.c:285: error: ‘B115200’ undeclared (first use in this function)
pl2303.c:286: error: ‘B230400’ undeclared (first use in this function)
pl2303.c:287: error: ‘B460800’ undeclared (first use in this function)
pl2303.c:303: error: ‘CSTOPB’ undeclared (first use in this function)
pl2303.c:311: error: ‘PARENB’ undeclared (first use in this function)
pl2303.c:317: error: ‘PARODD’ undeclared (first use in this function)
pl2303.c:329: error: dereferencing pointer to incomplete type
pl2303.c:329: error: dereferencing pointer to incomplete type
pl2303.c:335: error: dereferencing pointer to incomplete type
pl2303.c:337: error: ‘struct pl2303_private’ has no member named ‘line_control’
pl2303.c:339: error: ‘struct pl2303_private’ has no member named ‘line_control’
pl2303.c:340: error: dereferencing pointer to incomplete type
pl2303.c:340: error: ‘struct pl2303_private’ has no member named ‘line_control’
pl2303.c:340: error: too many arguments to function ‘set_control_lines’
pl2303.c:345: error: dereferencing pointer to incomplete type
pl2303.c:345: error: dereferencing pointer to incomplete type
pl2303.c:351: error: ‘CRTSCTS’ undeclared (first use in this function)
pl2303.c:352: error: ‘struct pl2303_private’ has no member named ‘driverType’
pl2303.c:353: error: dereferencing pointer to incomplete type
pl2303.c:353: error: dereferencing pointer to incomplete type
pl2303.c:358: error: dereferencing pointer to incomplete type
pl2303.c:358: error: dereferencing pointer to incomplete type
pl2303.c:365: warning: implicit declaration of function ‘kfree’
pl2303.c: At top level:
pl2303.c:369: warning: ‘struct file’ declared inside parameter list
pl2303.c:369: warning: ‘struct usb_serial_port’ declared inside parameter list
pl2303.c:370: error: conflicting types for ‘pl2303_open’
pl2303.c:102: error: previous declaration of ‘pl2303_open’ was here
pl2303.c: In function ‘pl2303_open’:
pl2303.c:371: error: storage size of ‘tmp_termios’ isn’t known
pl2303.c:372: error: dereferencing pointer to incomplete type
pl2303.c:375: error: dereferencing pointer to incomplete type
pl2303.c:377: warning: implicit declaration of function ‘port_paranoia_check’
pl2303.c:380: error: dereferencing pointer to incomplete type
pl2303.c:382: error: dereferencing pointer to incomplete type
pl2303.c:383: error: ‘struct pl2303_private’ has no member named ‘driverType’
pl2303.c:384: error: dereferencing pointer to incomplete type
pl2303.c:385: error: ‘struct pl2303_private’ has no member named ‘driverType’
pl2303.c:386: error: dereferencing pointer to incomplete type
pl2303.c:387: error: ‘struct pl2303_private’ has no member named ‘driverType’
pl2303.c:388: error: dereferencing pointer to incomplete type
pl2303.c:389: error: ‘struct pl2303_private’ has no member named ‘driverType’
pl2303.c:391: warning: implicit declaration of function ‘printk’
pl2303.c:391: error: ‘struct pl2303_private’ has no member named ‘driverType’
pl2303.c:403: error: dereferencing pointer to incomplete type
pl2303.c:403: error: dereferencing pointer to incomplete type
pl2303.c:404: error: dereferencing pointer to incomplete type
pl2303.c:404: error: dereferencing pointer to incomplete type
pl2303.c:404: error: ‘NULL’ undeclared (first use in this function)
pl2303.c:405: error: dereferencing pointer to incomplete type
pl2303.c:405: error: dereferencing pointer to incomplete type
pl2303.c:406: error: dereferencing pointer to incomplete type
pl2303.c:406: error: dereferencing pointer to incomplete type
pl2303.c:407: error: dereferencing pointer to incomplete type
pl2303.c:407: error: dereferencing pointer to incomplete type
pl2303.c:408: error: dereferencing pointer to incomplete type
pl2303.c:408: error: dereferencing pointer to incomplete type
pl2303.c:409: error: dereferencing pointer to incomplete type
pl2303.c:409: error: dereferencing pointer to incomplete type
pl2303.c:410: error: dereferencing pointer to incomplete type
pl2303.c:410: error: dereferencing pointer to incomplete type
pl2303.c:411: error: dereferencing pointer to incomplete type
pl2303.c:411: error: dereferencing pointer to incomplete type
pl2303.c:412: error: dereferencing pointer to incomplete type
pl2303.c:412: error: dereferencing pointer to incomplete type
pl2303.c:414: error: ‘struct pl2303_private’ has no member named ‘driverType’
pl2303.c:415: error: dereferencing pointer to incomplete type
pl2303.c:415: error: dereferencing pointer to incomplete type
pl2303.c:417: error: dereferencing pointer to incomplete type
pl2303.c:417: error: dereferencing pointer to incomplete type
pl2303.c:421: error: dereferencing pointer to incomplete type
pl2303.c:422: warning: passing argument 1 of ‘pl2303_set_termios’ from incompatible pointer type
pl2303.c:428: error: dereferencing pointer to incomplete type
pl2303.c:428: error: dereferencing pointer to incomplete type
pl2303.c:429: error: dereferencing pointer to incomplete type
pl2303.c:432: warning: passing argument 1 of ‘pl2303_close’ from incompatible pointer type
pl2303.c:437: error: dereferencing pointer to incomplete type
pl2303.c:437: error: dereferencing pointer to incomplete type
pl2303.c:438: error: dereferencing pointer to incomplete type
pl2303.c:441: warning: passing argument 1 of ‘pl2303_close’ from incompatible pointer type
pl2303.c: At top level:
pl2303.c:448: warning: ‘struct file’ declared inside parameter list
pl2303.c:448: warning: ‘struct usb_serial_port’ declared inside parameter list
pl2303.c:449: error: conflicting types for ‘pl2303_close’
pl2303.c:103: error: previous declaration of ‘pl2303_close’ was here
pl2303.c: In function ‘pl2303_close’:
pl2303.c:457: warning: implicit declaration of function ‘get_usb_serial’
pl2303.c:457: warning: assignment makes pointer from integer without a cast
pl2303.c:461: error: dereferencing pointer to incomplete type
pl2303.c:463: error: dereferencing pointer to incomplete type
pl2303.c:464: error: dereferencing pointer to incomplete type
pl2303.c:465: error: dereferencing pointer to incomplete type
pl2303.c:466: error: ‘HUPCL’ undeclared (first use in this function)
pl2303.c:468: error: dereferencing pointer to incomplete type
pl2303.c:469: error: ‘struct pl2303_private’ has no member named ‘line_control’
pl2303.c:470: error: dereferencing pointer to incomplete type
pl2303.c:471: error: ‘struct pl2303_private’ has no member named ‘line_control’
pl2303.c:471: error: too many arguments to function ‘set_control_lines’
pl2303.c:477: warning: implicit declaration of function ‘usb_unlink_urb’
pl2303.c:477: error: dereferencing pointer to incomplete type
pl2303.c:483: error: dereferencing pointer to incomplete type
pl2303.c:489: error: dereferencing pointer to incomplete type
pl2303.c: At top level:
pl2303.c:497: warning: ‘struct usb_serial_port’ declared inside parameter list
pl2303.c: In function ‘set_modem_info’:
pl2303.c:499: error: dereferencing pointer to incomplete type
pl2303.c:506: error: ‘TIOCMBIS’ undeclared (first use in this function)
pl2303.c:507: error: ‘TIOCM_RTS’ undeclared (first use in this function)
pl2303.c:508: error: ‘struct pl2303_private’ has no member named ‘line_control’
pl2303.c:509: error: ‘TIOCM_DTR’ undeclared (first use in this function)
pl2303.c:510: error: ‘struct pl2303_private’ has no member named ‘line_control’
pl2303.c:513: error: ‘TIOCMBIC’ undeclared (first use in this function)
pl2303.c:515: error: ‘struct pl2303_private’ has no member named ‘line_control’
pl2303.c:517: error: ‘struct pl2303_private’ has no member named ‘line_control’
pl2303.c:520: error: ‘TIOCMSET’ undeclared (first use in this function)
pl2303.c:523: error: ‘struct pl2303_private’ has no member named ‘line_control’
pl2303.c:524: error: ‘struct pl2303_private’ has no member named ‘line_control’
pl2303.c:525: error: ‘struct pl2303_private’ has no member named ‘line_control’
pl2303.c:529: error: dereferencing pointer to incomplete type
pl2303.c:529: error: ‘struct pl2303_private’ has no member named ‘line_control’
pl2303.c:529: error: too many arguments to function ‘set_control_lines’
pl2303.c: At top level:
pl2303.c:532: warning: ‘struct usb_serial_port’ declared inside parameter list
pl2303.c: In function ‘get_modem_info’:
pl2303.c:534: error: dereferencing pointer to incomplete type
pl2303.c:535: error: ‘struct pl2303_private’ has no member named ‘line_control’
pl2303.c:538: error: ‘TIOCM_DTR’ undeclared (first use in this function)
pl2303.c:539: error: ‘TIOCM_RTS’ undeclared (first use in this function)
pl2303.c:543: warning: implicit declaration of function ‘copy_to_user’
pl2303.c: At top level:
pl2303.c:548: warning: ‘struct file’ declared inside parameter list
pl2303.c:548: warning: ‘struct usb_serial_port’ declared inside parameter list
pl2303.c:549: error: conflicting types for ‘pl2303_ioctl’
pl2303.c:107: error: previous declaration of ‘pl2303_ioctl’ was here
pl2303.c: In function ‘pl2303_ioctl’:
pl2303.c:550: error: dereferencing pointer to incomplete type
pl2303.c:554: error: ‘TIOCMGET’ undeclared (first use in this function)
pl2303.c:555: error: dereferencing pointer to incomplete type
pl2303.c:556: warning: passing argument 1 of ‘get_modem_info’ from incompatible pointer type
pl2303.c:558: error: ‘TIOCMBIS’ undeclared (first use in this function)
pl2303.c:559: error: ‘TIOCMBIC’ undeclared (first use in this function)
pl2303.c:560: error: ‘TIOCMSET’ undeclared (first use in this function)
pl2303.c:561: error: dereferencing pointer to incomplete type
pl2303.c:562: warning: passing argument 1 of ‘set_modem_info’ from incompatible pointer type
pl2303.c:569: error: ‘ENOIOCTLCMD’ undeclared (first use in this function)
pl2303.c: At top level:
pl2303.c:573: warning: ‘struct usb_serial_port’ declared inside parameter list
pl2303.c:574: error: conflicting types for ‘pl2303_break_ctl’
pl2303.c:113: error: previous declaration of ‘pl2303_break_ctl’ was here
pl2303.c: In function ‘pl2303_break_ctl’:
pl2303.c:575: error: dereferencing pointer to incomplete type
pl2303.c:576: error: ‘u16’ undeclared (first use in this function)
pl2303.c:576: error: expected ‘;’ before ‘state’
pl2303.c:579: error: dereferencing pointer to incomplete type
pl2303.c:582: error: ‘state’ undeclared (first use in this function)
pl2303.c:587: error: dereferencing pointer to incomplete type
pl2303.c:587: error: dereferencing pointer to incomplete type
pl2303.c:589: error: ‘NULL’ undeclared (first use in this function)
pl2303.c: At top level:
pl2303.c:595: warning: ‘struct usb_serial’ declared inside parameter list
pl2303.c:596: error: conflicting types for ‘pl2303_shutdown’
pl2303.c:115: error: previous declaration of ‘pl2303_shutdown’ was here
pl2303.c: In function ‘pl2303_shutdown’:
pl2303.c:601: error: dereferencing pointer to incomplete type
pl2303.c:602: error: dereferencing pointer to incomplete type
pl2303.c: At top level:
pl2303.c:606: warning: ‘struct urb’ declared inside parameter list
pl2303.c:607: error: conflicting types for ‘pl2303_read_int_callback’
pl2303.c:108: error: previous declaration of ‘pl2303_read_int_callback’ was here
pl2303.c: In function ‘pl2303_read_int_callback’:
pl2303.c:608: error: dereferencing pointer to incomplete type
pl2303.c:609: warning: initialization makes pointer from integer without a cast
pl2303.c:619: error: dereferencing pointer to incomplete type
pl2303.c:620: error: dereferencing pointer to incomplete type
pl2303.c:624: error: dereferencing pointer to incomplete type
pl2303.c:624: error: dereferencing pointer to incomplete type
pl2303.c: At top level:
pl2303.c:633: warning: ‘struct urb’ declared inside parameter list
pl2303.c:634: error: conflicting types for ‘pl2303_read_bulk_callback’
pl2303.c:109: error: previous declaration of ‘pl2303_read_bulk_callback’ was here
pl2303.c: In function ‘pl2303_read_bulk_callback’:
pl2303.c:635: error: dereferencing pointer to incomplete type
pl2303.c:636: warning: initialization makes pointer from integer without a cast
pl2303.c:638: error: dereferencing pointer to incomplete type
pl2303.c:645: error: dereferencing pointer to incomplete type
pl2303.c:652: error: dereferencing pointer to incomplete type
pl2303.c:653: error: dereferencing pointer to incomplete type
pl2303.c:654: error: dereferencing pointer to incomplete type
pl2303.c:658: error: dereferencing pointer to incomplete type
pl2303.c:661: error: dereferencing pointer to incomplete type
pl2303.c:662: error: dereferencing pointer to incomplete type
pl2303.c:662: error: dereferencing pointer to incomplete type
pl2303.c:672: error: dereferencing pointer to incomplete type
pl2303.c:674: error: dereferencing pointer to incomplete type
pl2303.c:675: error: dereferencing pointer to incomplete type
pl2303.c:676: error: dereferencing pointer to incomplete type
pl2303.c:677: error: dereferencing pointer to incomplete type
pl2303.c:677: error: ‘TTY_FLIPBUF_SIZE’ undeclared (first use in this function)
pl2303.c:678: warning: implicit declaration of function ‘tty_flip_buffer_push’
pl2303.c:680: warning: implicit declaration of function ‘tty_insert_flip_char’
pl2303.c:686: error: dereferencing pointer to incomplete type
pl2303.c:687: error: dereferencing pointer to incomplete type
pl2303.c:687: error: dereferencing pointer to incomplete type
pl2303.c: At top level:
pl2303.c:698: warning: ‘struct urb’ declared inside parameter list
pl2303.c:699: error: conflicting types for ‘pl2303_write_bulk_callback’
pl2303.c:110: error: previous declaration of ‘pl2303_write_bulk_callback’ was here
pl2303.c: In function ‘pl2303_write_bulk_callback’:
pl2303.c:700: error: dereferencing pointer to incomplete type
pl2303.c:706: error: dereferencing pointer to incomplete type
pl2303.c:708: error: dereferencing pointer to incomplete type
pl2303.c:710: warning: implicit declaration of function ‘serial_paranoia_check’
pl2303.c:710: error: dereferencing pointer to incomplete type
pl2303.c:714: error: dereferencing pointer to incomplete type
pl2303.c:715: error: dereferencing pointer to incomplete type
pl2303.c:716: error: dereferencing pointer to incomplete type
pl2303.c:716: error: dereferencing pointer to incomplete type
pl2303.c:717: error: dereferencing pointer to incomplete type
pl2303.c:724: warning: implicit declaration of function ‘queue_task’
pl2303.c:724: error: dereferencing pointer to incomplete type
pl2303.c:724: error: ‘tq_immediate’ undeclared (first use in this function)
pl2303.c:725: warning: implicit declaration of function ‘mark_bh’
pl2303.c:725: error: ‘IMMEDIATE_BH’ undeclared (first use in this function)
pl2303.c: At top level:
pl2303.c:731: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘pl2303_init’
pl2303.c:739: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘pl2303_exit’
pl2303.c:745: warning: data definition has no type or storage class
pl2303.c:745: warning: type defaults to ‘int’ in declaration of ‘module_init’
pl2303.c:745: warning: parameter names (without types) in function declaration
pl2303.c:746: warning: data definition has no type or storage class
pl2303.c:746: warning: type defaults to ‘int’ in declaration of ‘module_exit’
pl2303.c:746: warning: parameter names (without types) in function declaration
pl2303.c:748: error: expected declaration specifiers or ‘...’ before string constant
pl2303.c:748: warning: data definition has no type or storage class
pl2303.c:748: warning: type defaults to ‘int’ in declaration of ‘MODULE_DESCRIPTION’
pl2303.c:748: warning: function declaration isn’t a prototype
pl2303.c:749: error: expected declaration specifiers or ‘...’ before string constant
pl2303.c:749: warning: data definition has no type or storage class
pl2303.c:749: warning: type defaults to ‘int’ in declaration of ‘MODULE_LICENSE’
pl2303.c:749: warning: function declaration isn’t a prototype
pl2303.c:751: error: expected ‘)’ before string constant
pl2303.c:752: error: expected ‘)’ before string constant
make: *** [pl2303.o] Error 1
chris@laptop:~/Documents/Softs/UsbtoSerial/Disk/Redhat9$ 

```

not much good happening here...:)

---

