---
title: "dapper killed my ethernet"
date: 2006-07-14
forum: General Help
---

### Post by Xoctor on 2006-07-14
I used to run Breezy on my Dell 7000 laptop. It ran well, but Dapper looked so great I had to install it. Not such a good idea. Now my network interface isn't recognised.

I have a Xircom ethernet/modem PCMCIA card. It worked out of the box on Breezy. On Dapper, I have to physically eject the PCMCIA card and reinsert it to get have it detected. There must be a solution to this, or at least a better workaround... any ideas?

xoctor.

---

### Post by Xoctor on 2006-07-16
I don't know if this is related, but I also get the following error above my Alt-F1 terminal screen:

ACPI: Unable to locate RSDP

Breezy ran flawlessly, so it seems odd that an upgrade would introduce these problems... but perhaps my hardware is getting old and support has been dropped?

Some help would REALLY be appreciated.

Regards,

xoctor.

---

### Post by bforbes on 2006-07-17
When it is not working, do the following, and post the output from it:
```

lspci
ifconfig
ifdown eth0
ifup eth0
ifconfig

```

---

### Post by Xoctor on 2006-07-17
Hi bforbes. Thanks for helping me out. In my searching, I found quite a few people asking the same question, but no answers, so it would be great to track down the problem.

Here is the output from the above commands:

```

lspci
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02)
0000:00:04.0 CardBus bridge: Texas Instruments PCI1220 (rev 02)
0000:00:04.1 CardBus bridge: Texas Instruments PCI1220 (rev 02)
0000:00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:08.0 Multimedia audio controller: ESS Technology ES1968 Maestro 2
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)


ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:600 (600.0 b)  TX bytes:600 (600.0 b)


ifdown eth0
ifdown: interface eth0 not configured


ifup eth0
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
SIOCSIFBRDADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Failed to bring up eth0.


ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:800 (800.0 b)  TX bytes:800 (800.0 b)

```
-------------------------------------------
AFTER ejecting PCMCIA card and reinserting:
```

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:A4:F1:26:F1
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::210:a4ff:fef1:26f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:64 (64.0 b)  TX bytes:767 (767.0 b)
          Interrupt:3 Base address:0x300

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:800 (800.0 b)  TX bytes:800 (800.0 b)


lspci
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02)
0000:00:04.0 CardBus bridge: Texas Instruments PCI1220 (rev 02)
0000:00:04.1 CardBus bridge: Texas Instruments PCI1220 (rev 02)
0000:00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:08.0 Multimedia audio controller: ESS Technology ES1968 Maestro 2
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)

```

I hope it helps!

xoctor.

---

### Post by bforbes on 2006-07-17
Hmmm. Post the contents of /etc/network/interfaces.
Use code tags when you do:
[ code ]
blah blah blah
[ /code ]
But remove the spaces between the square brackets.

---

### Post by Xoctor on 2006-07-17
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.254

```

it used to be...

```

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp

```

...but I changed it, as the machine is being used as a webserver.

---

### Post by bforbes on 2006-07-18
I'm afraid this has me stumped. I've never used Linux on a laptop, so the PCMCIA stuff is a bit foreign to me. Hopefully someone else can help.

---

### Post by Xoctor on 2006-07-18
Thanks for trying. I suspect this is a problem Dapper has with all older laptops that use a PCMCIA ethernet card... I hope someone works it out and posts the solution here.

---

### Post by honeydew on 2006-07-19
I seem to be having the exact same problem. so bump bump, my card worked with the live cd, and on install with the lts version, but after the install it is undetected.. ](*,)  so... if anyone has anybright ideas, help me break/love/make/install/finger my wifi. :D 

o yah, I cant post the exact output I recieved from thoose same commands.. but it seemed generaly the same.

---

### Post by Xoctor on 2006-07-19
It was the same for me. For some reason the Dapper live cd installer did detect the pcmcia network card and automatically connected to the internet. Very strange that it no longer works once installed. I tried upgrading the kernel, but no joy there.

---

### Post by honeydew on 2006-07-20
have you tested breezy?  I havnt tested any other distrobutions, Im thinking of giving freebsd a try tonight, I have 6 of these laptops though, I was hoping to loan them to friends w/ out computers and get them hooked on ubuntu.  Also one is going to the coffee shop I work at as a free internet terminal..

the model of my machine is IBM 600,    I tested one with a ethernet(not wifi) pcmcia card a while ago and it seemed to work.

please if anyone has any ideas it would be greatly appreciated

---

### Post by Xoctor on 2006-07-20
I used to run Breezy on this laptop. The network worked perfectly.

---

### Post by honeydew on 2006-07-20
I dont nessicarily want to give up on dapper quite yet, it holds alot of stability that I wish to  attain through its use :-#

---

### Post by zxee on 2006-07-20
Well just for the peversity of it I'll plug my poll:
[http://www.ubuntuforums.org/showthread.php?t=195283](http://www.ubuntuforums.org/showthread.php?t=195283)
I am also bothered by the incongruity of how well networking worked in breezy only to find dapper abysmal in that regard.

---

### Post by Xoctor on 2006-07-21
Sometimes I surprise myself. I actually solved this annoyance. Its not the neatest solution imaginable, but its not too bad either. 

You need to add a command to /etc/rc.local somewhere where it will be executed. Specifically, from a terminal type:
```

sudo vi /etc/rc.local

```
and put the following just above the 'exit 0' on the last line.
```

pccardctl eject
pccardctl insert

```

And there you have it!

---

### Post by Xoctor on 2006-07-21
I'm on a roll! :-)

This error (ACPI: Unable to locate RSDP) went away when I upgraded my kernel to 2.6.15-26-686.

I'm not sure why the powers that be use the 386 kernel by default. A 686 processor (Pentium Pro) is the absolute minimum requirement for usable GUI performance. Anyone with a processor older than a 686 would not want to run an Ubuntu default install.

---

