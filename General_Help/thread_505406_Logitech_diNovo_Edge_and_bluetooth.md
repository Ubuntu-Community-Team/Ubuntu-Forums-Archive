---
title: "Logitech diNovo Edge and bluetooth"
date: 2007-07-20
forum: General Help
---

### Post by hhdk on 2007-07-20
This keyboard just worked right out of the box (Ubuntu 7.04), amazing.
But, since I have a bluetooth enabled cellphone, I was wondering if the phone could connect to the computer through the usb bluetooth dongle, but I just can't figure out how.

I've installed all kind of bluetooth stuff, bluez-utils, bluez-gnome, bluetooth, gnome-bluetooth.
But none of them reconizes the dongle.

I once had a regular bluetooth dongle, and I got that working.

I get the following by running:
hh@hh-desktop:~$ dmesg | grep BT
```

[   44.778106] input: Logitech Logitech BT Mini-Receiver as /class/input/input3
[   44.778159] input: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:03.2-1.2
[   44.849916] input: Logitech Logitech BT Mini-Receiver as /class/input/input4
[   44.850083] input,hiddev96: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:03.2-1.3
[ 2376.122147] input: Logitech Logitech BT Mini-Receiver as /class/input/input8
[ 2376.122194] input: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:03.2-1.2
[ 2376.477269] input: Logitech Logitech BT Mini-Receiver as /class/input/input9
[ 2376.477376] input,hiddev96: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:03.2-1.3

```

And running this I get:
hh@hh-desktop:~$ lsusb
```

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 007: ID 046d:c714 Logitech, Inc. 
Bus 003 Device 006: ID 046d:c713 Logitech, Inc. 
Bus 003 Device 005: ID 046d:0b04 Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

```

Is it even possible to use this "Logitech BT Mini-receiver" to any other product than the diNovo Edge keyboard?
Like a regular bluetooth dongle?


- HHDK

---

### Post by da Wookiee on 2007-11-28
Just got an edge myself, in fact I'm typing on it right now.  If anyone has any experiences I'm sure we'd all like to hear.

My case it's a bluetooth headset, not a phone, but the same principle should follow.

---

### Post by da Wookiee on 2007-12-01
Well, I've searched a little, and all info I can find indicates that the dongle that comes with the edge is a dedicated edge that cannot be connected to anything else.  Now I'm wondering if I can get a 3rd Party BT dongle that will allow me to use the edge to get into the bios.  Any answers?

---

### Post by tenjin1 on 2007-12-02
I am also curious to know if my bluetooth dongle (Kensington) will work with the Logitech diNovo Edge Keyboard. I do not have a edge keyboard yet, but plan on getting one soon. The Bluetooth dongle I use now is for my kensington bluetooth mouse, which works great; but as I'm reading this the bluetooth dongle that comes with the edge keyboard is only specific to the edge keyboard....thats why I'm wanting to know if anyone is using a 3rd party dongle, which I have, to connect the edge keyboard?

---

### Post by da Wookiee on 2007-12-02
[http://www.amazon.com/exec/obidos/tg/detail/-/B000BVM8BW/ref=ord_cart_shr?%5Fencoding=UTF8&m=ATVPDKIKX0DER&v=glance](http://www.amazon.com/exec/obidos/tg/detail/-/B000BVM8BW/ref=ord_cart_shr?%5Fencoding=UTF8&m=ATVPDKIKX0DER&v=glance)

Actually This is the only dongle I've found that's said to work with this.  

[http://www.anycom.com/products/bluetooth_it_pc_accessoires/?id=102&group_id=3](http://www.anycom.com/products/bluetooth_it_pc_accessoires/?id=102&group_id=3)

Apparently it uses something called USB Hub Extension. It's what allows the mouse and keyboard to be detected at boot time.

---

