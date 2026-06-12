---
title: "usb's not working"
date: 2008-05-24
forum: General Help
---

### Post by tweekd1 on 2008-05-24
all of my usbs worked right after i installed Ubuntu for the first time. after i turned off the pc and came back to it, none of the usbs worked. this just includes my mouse and network adapter. i tried lsusb but i got all zeros meaning none of my usbs are detecting right? any help would be appreciated.

---

### Post by xfceuser on 2008-05-24
there might be a problem with one of your USB devices, remove all, restart, and then connect one by one and see which one makes the problem (maybe network card)

---

### Post by tweekd1 on 2008-05-24
how would i go about doing that?

---

### Post by xfceuser on 2008-05-24
just disconnect everything usb, then restart the computer.
now add the usb stuff again one by one (start from mouse) and see when it not work anymore.

---

### Post by tweekd1 on 2008-05-24
nothing..are there any commands that'll access the usb ports or anything?

---

### Post by mc4man on 2008-05-24
maybe try shutting down and unplugging your pc's power cord, hit the start button, wait a min, plug the power cord in  and boot up.

---

### Post by tweekd1 on 2008-05-24
> **mc4man said:**
> maybe try shutting down and unplugging your pc's power cord, hit the start button, wait a min, plug the power cord in  and boot up.

didnt work...the problem im getting is that theres no response from any usb ports. the light on my usb mouse turns on but doesnt work, and my usb network adapter doesnt do anything at all

---

### Post by tweekd1 on 2008-05-24
bump anybody?

---

### Post by xfceuser on 2008-05-24
you seem yo have problem with usb driver of linux or hardware problem.
open a Terminal. disconnect the mouse. now connect the mouse, and not much later type "dmesg" in the terminal. let us know what message at the end of the messages are about usb or easier use
dmesg | grep "usb"

---

### Post by strabes on 2008-05-24
Open a terminal (Applications > Accessories > Terminal) and paste the following command by selecting it (with a triple click) and pasting it by middle clicking in the terminal window.```
sudo modprobe ehci-hcd
```

---

### Post by tweekd1 on 2008-05-24
> **xfceuser said:**
> you seem yo have problem with usb driver of linux or hardware problem.
open a Terminal. disconnect the mouse. now connect the mouse, and not much later type "dmesg" in the terminal. let us know what message at the end of the messages are about usb or easier use
dmesg | grep "usb"

i got 

[26.971279] usbcore: registered new interface driver usbfs
[26.971308] usbcore: registered new interface driver hub
[26.985301] usbcore: registered new device driver usb
[26.994977] usb usb1: configuration #1 chosen from 1 choice
[27.095525] usb usb2: configuration #1 chosen from 1 choice
[27.199533] usb usb3: configuration #1 chosen from 1 choice
[27.323221] usb usb4: configuration #1 chosen from 1 choice

---

### Post by tweekd1 on 2008-05-24
> **strabes said:**
> Open a terminal (Applications > Accessories > Terminal) and paste the following command by selecting it (with a triple click) and pasting it by middle clicking in the terminal window.```
sudo modprobe ehci-hcd
```

when i did that, it asked for my password, i entered it in, then nothing happened. i tried doing it again and nothing happened.

---

### Post by tweekd1 on 2008-05-25
bumping because im stumped..

---

### Post by tweekd1 on 2008-05-25
any other ideas?

---

