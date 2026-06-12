---
title: "Keyboard and mouse dies at log-in screen 12.04"
date: 2014-02-03
forum: General Help
---

### Post by Brothir on 2014-02-03
I'm trying to install Ubuntu 12.04 for my very first time. I've tried wubi and mounting the official .iso from Win7, version 13 and 12.04/12.10, but the same problem persists: my mouse and keyboard dies at the log-in screen. Everything works perfectly fine in Win7 and when choosing OS at the startup screen, but the mouse becomes entirely unresposnive and the keyboard flat out dies. I've tried a Logitech G7 mouse and a standard-issue Microsoft mouse, a standard Microsoft keyboard and a Dell keyboard to no avail.

Computer details: 

AMD FX-6300 6-Core Processor
Motherboard: Gigabyte 970A-D3P, Socket-AM3+ATX, 970+SB950, DDR3, 2xPCIe-x16, CFX, SATA6Gb/s, USB 3.0, UEF
Corsair Vengeance DDR3 1600MHz 8GB

Any ideas?

---

### Post by PotatoHead007 on 2014-02-03
This may help [http://askubuntu.com/questions/314873/ubuntu-12-04lts-stuck-at-login-mouse-and-keyboard-not-responding](http://askubuntu.com/questions/314873/ubuntu-12-04lts-stuck-at-login-mouse-and-keyboard-not-responding)
Hope you manage :) Any questions about the commands, just ask :)

---

### Post by Brothir on 2014-02-03
I did see that thread, but I'm not sure if it's applicable to my situation seeing as his used to work then stopped, whereas mine never did.

Also, literally every step of that solution is gibberish to me :confused:

---

### Post by PotatoHead007 on 2014-02-03
> **Brothir said:**
> I did see that thread, but I'm not sure if it's applicable to my situation seeing as his used to work then stopped, whereas mine never did.

Also, literally every step of that solution is gibberish to me :confused:

Ok, try this(i do not know if this will not break your install, but its broken anyway i guess):

Boot from a live CD, then run the following(in a terminal):
```

sudo mkdir /mnt/temp-chroot
sudo mount /dev/sda5 /mnt/temp-chroot
sudo mount -t proc none /mnt/temp-chroot/proc
sudo chroot /mnt/temp-chroot su
dpkg --configure -a
apt-get update
apt-get upgrade
apt-get dist-upgrade

```

Really hope this works, if not, tell me so :)

---

### Post by ajgreeny on 2014-02-03
Make sure you use the correct /dev/sda[COLOR=#ff0000]5[/COLOR], so if yours is some other partition to sda5 use that instead.

---

### Post by Brothir on 2014-02-03
How do I know if it's different from dev/sda5?

---

### Post by bc.haynes on 2014-02-03
use the command in Terminal:
```
lsblk
```

---

### Post by PotatoHead007 on 2014-02-03
@ **bc.haynes and ajgreeny **thanks for that, i was a bit stuck there :P

---

