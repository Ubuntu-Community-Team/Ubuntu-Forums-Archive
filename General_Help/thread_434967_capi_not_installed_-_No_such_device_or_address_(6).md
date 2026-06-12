---
title: "capi not installed - No such device or address (6)"
date: 2007-05-06
forum: General Help
---

### Post by kwhitefoot on 2007-05-06
Not sure where to put this or what title to give it.  

My problem is that I want to use my ISDN card as an answering machine.  I sort of had it working-ish on SuSE with vbox but when I scrapped SuSE 10.2 in favour of Ubuntu 7.04 I have had no luck at all.  I've tried both vbox and capisuite with no success.

If I install CapiSuite via Synaptic and the issue capiinfo I get this response:

root@radar:~# capiinfo 
capi not installed - No such device or address (6)

Installing isdnutils etc. gives this:
 
root@radar:~# cat /dev/isdninfo
idmap:  - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 
chmap:  -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 
drmap:  -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 
usage:  0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 
flags:  ? ? ? ? ? ? ? ? ? ? ? ? ? ? ? ? ? ? ? ? ? ? ? ? ? ? ? ? ? ? ? ? 
phone:  ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? ??? 

isdnctrl gives this:

root@radar:~# isdnctrl -V
isdnctrl version 3.10
Kernel's view of API-versions:
ttyI: 6, net: 6, info: 1
root@radar:~# isdnctrl status /dev/ttyI0
Can't open /dev/isdnctrl or /dev/isdn/isdnctrl: No such device
root@radar:~# isdnctrl status /dev/isdn0
Can't open /dev/isdnctrl or /dev/isdn/isdnctrl: No such device

but ls -l shows:

root@radar:~# ls -l /dev/isdn*
crw-rw---- 1 root dialout 45,   0 2007-05-06 12:06 /dev/isdn0
crw-rw---- 1 root dialout 45,   1 2007-05-06 12:06 /dev/isdn1
... omitted for brevity
crw-rw---- 1 root dialout 45,   9 2007-05-06 12:06 /dev/isdn9
lrwxrwxrwx 1 root root          9 2007-05-06 15:43 /dev/isdnctrl -> isdnctrl0
crw-rw---- 1 root dialout 45,  64 2007-05-06 12:06 /dev/isdnctrl0
crw-rw---- 1 root dialout 45,  65 2007-05-06 12:06 /dev/isdnctrl1
... omitted for brevity
crw-rw---- 1 root dialout 45, 255 2007-05-06 12:06 /dev/isdninfo

So my question is: does anyone have a recipe for getting Ubuntu 7.04 to work as an ISDN answering machine.

lspci shows this information about the isdn card:
01:07.0 Network controller: Cologne Chip Designs GmbH ISDN network controller [HFC-PCI] (rev 02)

I also tried connecting to the card with minicom.  The connection with  the card worked as I got sensible responses to at commands but when I tried to dial out I got:

NO DIALTONE  

:confused:

---

### Post by DikShinnery on 2007-06-29
I have almost exactly the same problem, my diagnostics are practically identical, using same ISDN card chipset,  on Ubuntu 7.04 - the Feisty Fawn.
I'm trying to get Asterisk running in our office and I can't get our ISND card working.

---

### Post by VMbuseck on 2007-07-03
I've got the same problem with dapper drake 6.06:

When I plug in the card:

```

.
Jul  3 12:12:19 localhost kernel: [17179693.356000] pcmcia: registering new device pcmcia0.0
Jul  3 12:12:19 localhost kernel: [17179693.464000] ISDN subsystem Rev: 1.1.2.3/1.1.2.3/1.1.2.2/1.1.2.3/1.1.2.2/1.1.2.2 loaded
Jul  3 12:12:19 localhost kernel: [17179693.524000] HiSax: Linux Driver for passive ISDN cards
Jul  3 12:12:19 localhost kernel: [17179693.524000] HiSax: Version 3.5 (module)
Jul  3 12:12:19 localhost kernel: [17179693.528000] HiSax: Layer1 Revision 2.46.2.5
Jul  3 12:12:19 localhost kernel: [17179693.528000] HiSax: Layer2 Revision 2.30.2.4
Jul  3 12:12:19 localhost kernel: [17179693.528000] HiSax: TeiMgr Revision 2.20.2.3
Jul  3 12:12:19 localhost kernel: [17179693.528000] HiSax: Layer3 Revision 2.22.2.3
Jul  3 12:12:19 localhost kernel: [17179693.528000] HiSax: LinkLayer Revision 2.59.2.4
Jul  3 12:12:20 localhost kernel: [17179693.536000] avma1_cs: testing i/o 0x140-0x147
Jul  3 12:12:20 localhost kernel: [17179693.580000] avma1_cs: checking at i/o 0x140, irq 3
Jul  3 12:12:20 localhost kernel: [17179693.580000] HiSax: Card 1 Protocol EDSS1 Id=HiSax (0)
Jul  3 12:12:20 localhost kernel: [17179693.580000] HiSax: AVM A1 PCMCIA driver Rev. 2.9.2.5
Jul  3 12:12:20 localhost kernel: [17179693.996000] AVM A1 PCMCIA: io 0x140 irq 3 model 1 version 2
Jul  3 12:12:20 localhost kernel: [17179693.996000] AVM A1 PCMCIA: ISAC version (0): 2086/2186 V1.1
Jul  3 12:12:20 localhost kernel: [17179693.996000] AVM A1 PCMCIA: HSCX version A: V2.1  B: V2.1
Jul  3 12:12:20 localhost kernel: [17179693.996000] AVM A1 (PCMCIA): IRQ 3 count 2
Jul  3 12:12:20 localhost kernel: [17179694.012000] AVM A1 (PCMCIA): IRQ 3 count 5
Jul  3 12:12:20 localhost kernel: [17179694.012000] HiSax: DSS1 Rev. 2.32.2.3
Jul  3 12:12:20 localhost kernel: [17179694.012000] HiSax: 2 channels added
Jul  3 12:12:20 localhost kernel: [17179694.012000] HiSax: MAX_WAITING_CALLS added
Jul  3 12:12:20 localhost kernel: [17179694.012000] HiSax: if_command 6 called with invalid driverId 0!
Jul  3 12:12:20 localhost kernel: [17179694.012000] HiSax: if_command 6 called with invalid driverId 0!
.

```

```

root@d510:~# isdnctrl -V
isdnctrl version 3.8
Kernel's view of API-versions:
ttyI: 6, net: 6, info: 1

```

The following additional packages are installed:
[list]
[*]avm_fritz_firmware (incl. capiutils)
[*]pppdcapiplugin
[*]isdnutils_base
[/list]

linux-restricted-modules was already installed.

Dialing:

```

mick@d510:/$ pon isdn/avm
Plugin userpass.so loaded.
userpass: $Revision: 1.5 $
Plugin capiplugin.so loaded.
capiplugin: $Revision: 1.36 $
capiconn:  1.13
capiplugin: CAPI_REGISTER failed - CAPI not installed (0x1009) [No such device or address (6)]

```

---

### Post by suoko on 2007-07-06
no solution at all?
ubuntu devs should probably consider that ISDN connection through a simple  ISDN card is a cheap backup internet connection in case of ADSL failure and that it is NEEDED in all companies (small, medium and large ones).

I'd like to use the slow 56k external modem instead of ISDN but the new pc has no COM port!
Is it really time to go back to fedora?

---

### Post by VMbuseck on 2007-07-10
[SIZE="4"][COLOR="Red"]Did anybody known's the solution ???[/COLOR][/SIZE]

---

### Post by VMbuseck on 2007-07-22
I've downloaded the original driver from AVM (fcpcmcia-suse93-3.11-07.tar.gz) and compiled the driver

```
make -C src
```

After that I executed the install script

```
./install
```

Everything seems to be ok.

Adding the fcpcmcia in /etc/isdn/capi.conf will load the driver, when the CAPI comes up.

```
root@d510:/# lsmod | grep fc
rfcomm                 40216  0
l2cap                  26372  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
fcpcmcia              591800  0
kernelcapi             48288  3 fcpcmcia,capi,capidrv
```

But the card will not work at all

```
root@d510:/# pon isdn/avm
Plugin userpass.so loaded.
userpass: $Revision: 1.5 $
Plugin capiplugin.so loaded.
capiplugin: $Revision: 1.36 $
capiconn:  1.13
capiplugin: CAPI_REGISTER failed - CAPI not installed (0x1009) [No such device or address (6)]

```

---

