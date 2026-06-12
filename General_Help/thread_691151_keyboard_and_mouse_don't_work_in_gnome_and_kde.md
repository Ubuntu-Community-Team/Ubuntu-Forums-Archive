---
title: "keyboard and mouse don't work in gnome and kde"
date: 2008-02-08
forum: General Help
---

### Post by Man of Wax on 2008-02-08
Hi all... very strange problem here!
My keyboard and mouse don't work after logging in in ubuntu and kubuntu. In gdm/kdm both keyboard and mouse work well but after the login mouse stop working instantly and after few minutes the keyboard doesn't work anymore... Same problem with Kde. Fluxbox works very well instead.

I tried fedora 8 (gnome spin)  and I got the same problem...

---

### Post by neurostu on 2008-02-08
Are your keyboards USB or PS/2. Are they regular run of the mill, or are the specialized?

---

### Post by Man of Wax on 2008-02-09
> **neurostu said:**
> Are your keyboards USB or PS/2. Are they regular run of the mill, or are the specialized?

To tell the truth a friend of mine has this problem not me... anyway he has a standard 3-buttons usb mouse and an ergonomic microsoft usb keyboard: [http://www.microsoft.com/hardware/mouseandkeyboard/productdetails.aspx?pid=067](http://www.microsoft.com/hardware/mouseandkeyboard/productdetails.aspx?pid=067) 
the layout is the same of this one without the wireless feature.

P.s: don't complain about the microsoft keyboard... I've already done it for you :D

---

### Post by neurostu on 2008-02-09
The only reason I asked is that sometimes really speciallized keyboards and mice require special drivers, but this time it doesn't seem that that is the case.

Is the keyboard ps/2 or usb?

Try getting another keyboard and mouse and see if they work. Then once you have a working keyboard and mouse plug the good ones and the bad ones in and run:
```
 $lsusb 
```

---

### Post by Man of Wax on 2008-02-10
ok more news:
the keyboard work well, the mouse don't...
The mouse sometime doesn't work... this is the dmesg output when it works:
```

[  571.539854] usb 1-2: new low speed USB device using ohci_hcd and address 4
[  571.754080] usb 1-2: configuration #1 chosen from 1 choice
[  571.764185] input: Microsoft Basic Optical Mouse as /class/input/input7
[  571.764263] input: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:0b.0-2

```

And this is the output when not:
```

[  757.085460] ohci_hcd 0000:00:0b.0: IRQ INTR_SF lossage
[  757.085469] ohci_hcd 0000:00:0b.0: leak ed f7d36100 (#81) state 0 (has tds)

```
When the mouse doesn't work the lsubs hangs and i can't retrieve any input. Any clue?

---

