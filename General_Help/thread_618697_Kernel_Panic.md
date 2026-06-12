---
title: "Kernel Panic?"
date: 2007-11-20
forum: General Help
---

### Post by shootdamonkey on 2007-11-20
I keep getting the kernel panic message everytime i try and boot into ubuntu from grub, so i thought i'd use the live cd to try and get things working again and yet i still get the kernel panic message with the cd. Is it something to do with my system? and how can i resolve this problem?

(i have searched the forum and google and being somewhat of a noob i cant seem to find a solution)

---

### Post by colo on 2007-11-20
There are quite a few possibilites for a kernel panic on boot, amongst them grave things like Machine Check Exceptions, and more commonly seen ones, like lacking of drivers vital for the system to access the / filesystem. You need to supply the _exact_ kernel panic error message to get reliable help here or anywhere else.

---

### Post by stoodleysnow on 2007-11-21
Kernel Panic - Not synching: Fatal Exception In Interrupt
I get when I try to boot an MSI 5182 based machine from LiveCD.
:confused:

---

### Post by colo on 2007-11-21
Try booting with all combinations of the following kernel parameters:

noapic nolapic noacpi

If that does not work, try disabling all integrated peripherals you don't need in your motherboards's BIOS setup, remove all PCI-cards you don't need, and try booting up again - also with any combination of said parameters.

---

### Post by steve_steve on 2008-04-20
I was just getting the same error: Kernel Panic - Not synching: Fatal Exception In Interrupt.

It turns out that it was the cpu over-heating.  A fan wired had snuck into the fan blades preventing it from turning.  Removed wire, let it cool, and it's back up & running.

Just something else to check.

---

