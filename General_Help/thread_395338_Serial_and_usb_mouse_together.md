---
title: "Serial and usb mouse together"
date: 2007-03-28
forum: General Help
---

### Post by richbiskit on 2007-03-28
Hey guys, i have a problem!

I have just installed ubuntu edgy on an old PC and am using a usb mouse. the pc only has one usb port so when i use my usb printer i have to unplug the mouse. i have re-configured xorg.conf to use a serial mouse by doing this..

Option "Device" "/dev/ttyS0"
Option "Protocol" "Microsoft"

 that works fine but now the usb mouse wont work. i guess i need to make it know that there is a mouse on both serial and usb........ how? any help would be most welcome!

---

### Post by mahy on 2007-03-28
This works for me:

USB mouse: /dev/input/mice; protocol: ExplorerPS/2

PS/2 mouse (Synaptics Touchpad): /dev/psaux; protocol: auto-dev

---

### Post by richbiskit on 2007-03-28
Thanks mahy, it's my girlfriends PC so i cant try it till later but i will let you know :)

---

### Post by richbiskit on 2007-03-29
no luck so far :(  Mahy, can you post your xorg.conf so i can see, i am not sure where i am supposed to put everything! :lolflag:

---

