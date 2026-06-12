---
title: "problem with external mouse and keyboard on USB on 16.04 Ubuntu Mate"
date: 2018-02-25
forum: General Help
---

### Post by kpapadim on 2018-02-25
Hello all, 

The following problem appeared gradually, not from the beginning that i installed 16.04. It appeared while I was doing updates, around 1 month ago. 

While I am working on the laptop, the external usb mouse and keyboard stop responding  completely, e.g. the cursor freezes. Laptop's keyboard operates fine always, and also always (almost) the laptop's touchpad.

Temporary workaround is suspending the system, then turn-it on again. Usually, everything works, for some time. Then again...I have to suspend and the story goes on.

system's details are:

  
[LIST]
[*]OS: Ubuntu Mate 16.04.4 LTS 
[*]laptop: DELL latitude e6420 
[*]kernel: 4.13.0-36-generic 
[*]VM VirtualBox 
[/LIST]
  
Any solution on this?

Regarding other devices that I have tried on usb, e.g. usb stick, seem to work without any issues.
 

Thanks,
kpapadim

---

### Post by kpapadim on 2018-02-27
Hello again

had anyone faced the same problem?
it never appeared when I was running Ubuntu 10.04 and 12.04 

thanks

---

### Post by oldrocker99 on 2018-02-27
Hmmm. I've never at all had any problem with mouse and keyboard unresponsiveness, except when I was dual-booting with Windows. You know the drill: No mouse pointer at the login screen, boot to Safe mode, the mouse works, reboot and the mouse pointer is frozen. Again.

You might try another keyboard and mouse; it could be a hardware problem.

---

### Post by gmolleda on 2018-03-04
Cambiando el dispositivo de USB a otro USB trabaja de nuevo, si es el ratón a mi me funciona hacer desde la terminal (control+alt+t):

echo -n "0000:00:1d.0" | sudo tee /sys/bus/pci/drivers/ehci-pci/unbind
echo -n "0000:00:1d.0" | sudo tee /sys/bus/pci/drivers/ehci-pci/bind

Para no escribir tanto me hice un script bash (simplemente copia y pega en un editor de texto simple como xed, gedit, nano...):

#!/bin/bash

echo -n "0000:00:1d.0" | tee /sys/bus/pci/drivers/ehci-pci/unbind
echo -n "0000:00:1d.0" | tee /sys/bus/pci/drivers/ehci-pci/bind

Lo guardas en tu carpeta personal /home/TUUSUARIO con un nombre, por ejemplo ponraton.sh y lo haces ejecutable con el botón derecho de ratón sobre el mismo, en propiedades u Opciones - Permisos y marcas lo de ejectuar, en terminal sería: $ chmod 755 ponraton.sh Y ahora puedes ejecutar con sudo: primero Control+Alt+T en el teclado te abre la terminal y usas sudo ./ponraton.sh

Me pasa de hace poco para acá, igual desde el paso del kernel al 4.13 desde 4.4 por culpa del fallo de los procesadores.

---

### Post by The Cog on 2018-03-04
Google translates the above post to:
Changing the USB device to another USB works again, if the mouse is working for me from the terminal (control + alt + t):

echo -n "0000: 00: 1d.0" | sudo tee / sys / bus / pci / drivers / ehci-pci / unbind
echo -n "0000: 00: 1d.0" | sudo tee / sys / bus / pci / drivers / ehci-pci / bind

To not write so much I made a bash script (simply copy and paste in a simple text editor such as xed, gedit, nano ...):

#! / bin / bash

echo -n "0000: 00: 1d.0" | tee / sys / bus / pci / drivers / ehci-pci / unbind
echo -n "0000: 00: 1d.0" | tee / sys / bus / pci / drivers / ehci-pci / bind

You save it in your personal folder / home / TUUSUARIO with a name, for example ponraton.sh and you do it executable with the right mouse button on it, in properties or Options - Permissions and marks what to execute, in terminal it would be: $ chmod 755 ponraton.sh And now you can run with sudo: first Control + Alt + T on the keyboard opens the terminal and you use sudo ./ponraton.sh

I happen recently for here, the same since the passage of the kernel to 4.13 from 4.4 because of the failure of the processors.

---

### Post by kpapadim on 2018-03-27
well, i tried these commands, but they didn't fix the problem
echo -n "0000: 00: 1d.0" | sudo tee / sys / bus / pci / drivers / ehci-pci / unbind
echo -n "0000: 00: 1d.0" | sudo tee / sys / bus / pci / drivers / ehci-pci / bind

I tried them on 4.13.0-37-generic

I decided to check booting with an older kernel, 4.13.0-32-generic, no problem with this kernel, everything is functioning...at still for now!

kp

---

### Post by pechter2 on 2018-04-20
I am seeing the same problem since I upgraded from 17.04 to 17.10 and now 18.04.

However, if I boot from a USB with the 18.04 beta on it it works fine:

Bus 008 Device 002: ID 045e:009d Microsoft Corp. Wireless Optical Desktop 3.0
  idVendor           0x045e Microsoft Corp.
  iManufacturer           1 Microsoft
  iProduct                2 Microsoft Wireless Optical Desktop® 2.10

If I booted the 18.04 from my hard disk -- the only keyboard and mouse are the Lenovo USB keyboard and USB mouse (disconnected at present to test the Microsoft
stuff from the same port).

root@ubuntu:~# dmesg -T | grep -i  mouse
[Fri Apr 20 04:09:47 2018] mousedev: PS/2 mouse device common for all mice
[Fri Apr 20 04:09:48 2018] microsoft 0003:045E:009D.0002: input,hidraw1: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Desktop® 2.10] on usb-0000:00:1d.3-2/input1
root@ubuntu:~# dmesg -T | grep -i keyboard
[Fri Apr 20 04:09:48 2018] microsoft 0003:045E:009D.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft Wireless Optical Desktop® 2.10] on usb-0000:00:1d.3-2/input0
[Fri Apr 20 04:09:48 2018] usb 1-1.4.4: Product: Lenovo USB Keyboard
[Fri Apr 20 04:09:48 2018] input: Lite-On Technology Corp. Lenovo USB Keyboard as /devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1.4/1-1.4.4/1-1.4.4:1.0/0003:17EF:6018.0003/input/input7
[Fri Apr 20 04:09:48 2018] hid-generic 0003:17EF:6018.0003: input,hidraw2: USB HID v1.10 Keyboard [Lite-On Technology Corp. Lenovo USB Keyboard] on usb-0000:00:1a.7-1.4.4/input0
[Fri Apr 20 04:09:48 2018] input: Lite-On Technology Corp. Lenovo USB Keyboard as /devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1.4/1-1.4.4/1-1.4.4:1.1/0003:17EF:6018.0004/input/input8
[Fri Apr 20 04:09:48 2018] hid-generic 0003:17EF:6018.0004: input,hidraw3: USB HID v1.10 Device [Lite-On Technology Corp. Lenovo USB Keyboard] on usb-0000:00:1a.7-1.4.4/input1

Any thoughts.  The boxes involved (two different Lenovo Workstation class Xeon boxes with USB 2.0) ran Ubuntu from 14.04 through 17.04 cleanly IIRC.  The problem seemed to
start with 17.10.

Bill

---

