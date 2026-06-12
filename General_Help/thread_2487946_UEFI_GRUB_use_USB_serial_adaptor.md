---
title: "UEFI GRUB use USB serial adaptor"
date: 2023-06-18
forum: General Help
---

### Post by starbuck666 on 2023-06-18
Hi

I have a headless dev server booting in UEFI mode (secure boot disabled) with 3 ubuntu variants installed which I can select from the GRUB2 boot menu.
I would like to make this server headless and select which OS to boot via a serial connection. I'm a little stuck because I don't understand GRUB well and I'm struggling with the documention.
My USB serial adaptor is supported by GRUB using using `insmod usbserial_pl2303`

If I drop to the grub command line and load the module I can see that it creates a new serial interface:

# before loading the modue
```
> **terminal_output**
Active output terminals:
console
Available output terminals:
gfxterm spkmodem serial
```


# after loading the module
```
> **insmod usbserial_pl2303**
> **terminal_output**
Active output terminals:
console
Available output terminals:
gfxterm spkmodem serial serial_com0
```

I then add the new interface to the terminal like this:

```

> **termial_input --append serial_com0**
Active output terminals:
console serial_com0
Available output terminals:
gfxterm spkmodem serial serial_com0
```

```

> **termial_output --append serial_com0**
Active output terminals:
console serial_com0
Available output terminals:
gfxterm spkmodem serial serial_com0
```

At this point I was expecting the serial port to start working, but there is no activity on the port.

Can anyone point me in the right direction?

---

