---
title: "trouble with LIRC and PCI serial adapter"
date: 2008-05-08
forum: General Help
---

### Post by cbaker on 2008-05-08
i'm having trouble getting LIRC to work with a pci serial adapter i bought.  can anyone offer me any advice?  i have a fresh hardy install.  
```
$ uname -r
2.6.24-16-generic
```

i have the X10 mouseremote (serial): [http://www.x10.com/products/x10_mk19a.htm](http://www.x10.com/products/x10_mk19a.htm)
connected to a CyberSerial PCI card from SIIG: [http://www.siig.com/ViewProduct.aspx?pn=JJ-P02D11-S6](http://www.siig.com/ViewProduct.aspx?pn=JJ-P02D11-S6)

it appears at first glance that i have the SIIG card setup correctly:
```
$ lspci -v
<relevant portion shown>
01:06.0 Serial controller: Oxford Semiconductor Ltd EXSYS EX-41092 Dual 16950 Serial adapter (prog-if 06 [16950])
	Subsystem: Siig Inc Unknown device 2530
	Flags: medium devsel, IRQ 16
	I/O ports at b000 [size=32]
	Memory at e5008000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at b400 [size=32]
	Memory at e5004000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [40] Power Management version 2

01:06.1 Bridge: Oxford Semiconductor Ltd OX16PCI954 (Quad 16950 UART) function 1 (Disabled)
	Subsystem: Siig Inc Unknown device 0000
	Flags: medium devsel, IRQ 10
	I/O ports at b800 [size=32]
	Memory at e5005000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at bc00 [size=32]
	Memory at e5006000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [40] Power Management version 2
```

```
$ setserial -bg /dev/ttyS*
/dev/ttyS0 at 0x03f8 (irq = 4) is a 16550A
/dev/ttyS1 at 0xb000 (irq = 16) is a 16950/954
/dev/ttyS2 at 0xb008 (irq = 16) is a 16950/954
```

and when i do a:
```
$ cat /dev/ttyS1
```

and start pushing buttons on my remote, i get a bunch of crap on stdout.  so it appears to be working.  however, after
```

$ sudo /etc/init.d/lirc stop
 * Stopping remote control daemon(s): LIRC          [ OK ] 
$ sudo lircd -n --device="/dev/ttyS1" --driver="mouseremote"
lircd-0.8.3pre1[7033]: lircd(userspace) ready
```

i don't get anything with `irw`.  

```
$ cat /etc/lirc/hardware.conf 
REMOTE="X10 MouseRemote RF Receiver (Serial)"
REMOTE_MODULES=""
REMOTE_DRIVER="mouseremote"
REMOTE_DEVICE="/dev/ttyS1"
REMOTE_LIRCD_CONF="x10/lircd.conf.mouseremote"
REMOTE_LIRCD_ARGS=""
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
LOAD_MODULES=""
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
```

```
$ cat /etc/lirc/lircd.conf
#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the X10 MouseRemote RF Receiver (Serial) remote:
include /usr/share/lirc/remotes/x10/lircd.conf.mouseremote
```

can anyone offer any suggestions?

---

