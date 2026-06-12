---
title: "How to install NVIDIA GeForce GT 720M with OUT Problem ubuntu 16.04.1 desktop amd64 ?"
date: 2016-09-23
forum: General Help
---

### Post by ahmadddddddd on 2016-09-23
[COLOR=#111111][FONT=Ubuntu]How to install NVIDIA GeForce GT 720M with OUT Problem ubuntu 16.04.1 desktop amd64 ?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Please Help Me How to install it ? My Laptop Acer Aspire E1-570G[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Screen: 15.6 inch Display [/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]RAM: 8 GB DDR3 [/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Procssor: Intel Core i3 (3rd Gen) ==> Intel(R) HD Graphics 4000 [/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Hard Disk: 500 GB HDD [/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Battery: 4 cell[/FONT][/COLOR]

---

### Post by howefield on 2016-09-23
Have you tried the "Additional Drivers" application, what drivers does it offer you ?

---

### Post by ahmadddddddd on 2016-09-23
im install with [COLOR=#000000]Additional Drivers[/COLOR]
but its Black Screen & Low Grapical Mod

---

### Post by Bashing-om on 2016-09-23
ahmadddddddd; Hello - My Welcome to the forum.

Indications are that the problem might be graphic's driver related. 
Let's take a look and see what we have to work with - what is installed :
Boot to the login screen and at this screen key combo ctl+alt+F1 to gain a console interface.
Log into the system with your credentials ( username and password, no response to the screen when password is entered - enter password blindly and hit the enter key ) .

As this console does not have the amenities of a terminal emulator we use a pastebin site to relay requested information:
In this interface execute terminal commands:
```

lspci -vnn | grep VGA -A 12 | nc termbin.com 9999
dpkg -l | grep -i nvidia | nc termbin.com 9999
lsmod | grep nvidia | nc termbin.com 9999

```
the results of these commands is a URL back in terminal, pass these links back here and we access these files to see the result of the terminal commands.
From this information we get an idea of where next to go and what to do.

[INDENT][INDENT]it's all in the process
[/INDENT][/INDENT]

---

### Post by ahmadddddddd on 2016-09-25
mr.Bashing-om

> aha@aha:~$ lspci -vnn | grep VGA -A 12 | nc termbin.com 9999
[http://termbin.com/01b3](http://termbin.com/01b3)
aha@aha:~$ dpkg -l | grep -i nvidia | nc termbin.com 9999
Use netcat.
aha@aha:~$ lsmod | grep nvidia | nc termbin.com 9999
Use netcat.
aha@aha:~$ 



> 00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] 3rd Gen Core processor Graphics Controller [1025:0835]
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Memory at b3000000 (64-bit, non-prefetchable) [size=4M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 3000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04) (prog-if 30 [XHCI])
	Subsystem: Acer Incorporated [ALI] 7 Series/C210 Series Chipset Family USB xHCI Host Controller [1025:0835]


---

### Post by Bashing-om on 2016-09-25
ahmadddddddd; Welp:

To this time we see no nVidia graphics; 
Let's see what:
```

lspci -k | grep -EA2 'VGA|3D' 

```
reveals for a "3D"  device .

[INDENT][INDENT]can not work with
[INDENT][INDENT][INDENT]what is not
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

