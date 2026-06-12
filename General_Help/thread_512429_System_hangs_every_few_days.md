---
title: "System hangs every few days"
date: 2007-07-29
forum: General Help
---

### Post by Eddy Dean on 2007-07-29
Hello,

My Ubuntu Feisty Fawn system crashes totally every few days. When this happens there is nothing I can do about it. I can't move my mouse, type anything. Everything just stops, including movies, animated GIFs, the clock etc.
It appears to be happening at random intervals, and I don't think it has to do with a program being loaded or w/e.  Today the computer hang while I was copying a DVD, but a few days ago it happened when I clicked the "Ubuntu" logo to get the main menu. Sometimes it happens right in the middle of watching a movie, or while doing nothing at all.

In /var/log/messages there are a lot of gconf messages, and a few bluetooth errors, even though my PC doesn't have bluetooth enabled.

The gconf errors look like this:
```
Jul 29 14:21:53 rechts gconfd (gezin-5242): Adres "xml:readonly:/etc/gconf/gconf.xml.mandatory" getraceerd naar een al
leen-lezen configuratiebron op positie 0
Jul 29 14:21:53 rechts gconfd (gezin-5242): Adres "xml:readwrite:/home/gezin/.gconf" getraceerd naar een schrijfbare c
onfiguratiebron op positie 1
Jul 29 14:21:53 rechts gconfd (gezin-5242): Adres "xml:readonly:/etc/gconf/gconf.xml.defaults" getraceerd naar een all
een-lezen configuratiebron op positie 2
Jul 29 14:21:53 rechts gconfd (gezin-5242): Adres "xml:readonly:/var/lib/gconf/debian.defaults" getraceerd naar een al
leen-lezen configuratiebron op positie 3
Jul 29 14:21:53 rechts gconfd (gezin-5242): Adres "xml:readonly:/var/lib/gconf/defaults" getraceerd naar een alleen-le
zen configuratiebron op positie 4

```

Translation of this: Address "blahblah" traced to an (schrijfbare = writable)/(alleen-lezen = read-only) configuration source at position #

And the bluetooth stuff looks like this: 
```
Jul 29 14:21:53 rechts kernel: [   58.309107] apm: BIOS not found.
Jul 29 14:21:54 rechts kernel: [   58.866806] Bluetooth: Core ver 2.11
Jul 29 14:21:54 rechts kernel: [   58.867485] NET: Registered protocol family 31
Jul 29 14:21:54 rechts kernel: [   58.867488] Bluetooth: HCI device and connection manager initialized
Jul 29 14:21:54 rechts kernel: [   58.867493] Bluetooth: HCI socket layer initialized
Jul 29 14:21:54 rechts kernel: [   58.966261] Bluetooth: L2CAP ver 2.8
Jul 29 14:21:54 rechts kernel: [   58.966267] Bluetooth: L2CAP socket layer initialized
Jul 29 14:21:54 rechts kernel: [   59.102220] Bluetooth: RFCOMM socket layer initialized
Jul 29 14:21:54 rechts kernel: [   59.102547] Bluetooth: RFCOMM TTY layer initialized
Jul 29 14:21:54 rechts kernel: [   59.102550] Bluetooth: RFCOMM ver 1.8

```

My system is the following:
ASRock motherboard with VIA USB/LPT/etc controller
AMD Athlon XP 2800+
nVidia GeForce 5200 (driver is installed and running)
1GB DDR2 RAM

I really have no idea what information would be relevant as well, it just seems to happen at random intervals, so I can't tell what's causing the problem.
Oh, ctrl-alt-backspace or ctrl-alt-delete don't work either (this should cause CPU interrupts, shouldn't they?)

---

### Post by Trosky on 2007-07-29
I had a similar problem one month ago, start with another kernel version, maybe it helps

---

### Post by Eddy Dean on 2007-07-29
You're right. Even though I already started blaming the kernel, I didn't try the older version that is still installed on my PC.

I'll reboot and try the other kernel, I'll report back on you later.

---

