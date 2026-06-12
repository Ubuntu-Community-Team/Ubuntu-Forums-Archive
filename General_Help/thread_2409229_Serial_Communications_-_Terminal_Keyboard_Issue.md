---
title: "Serial Communications - Terminal Keyboard Issue"
date: 2018-12-30
forum: General Help
---

### Post by n2te on 2018-12-30
Would anyone know if there is a serial communications terminal program available for the Linux platform (I'm running Ubuntu 18.04) that will allow me to customize the serial output data that is sent out the serial port when pressing any of the keyboard's F1-F12 function keys? I'm communicating with and controlling a legacy electronic device (details irrelevant) that has a serial communications port. Use of the function keys with this external device is not working correctly when utizling a serial terminal program on my PC. Use of the "standard" ASCII character keys on the keyboard works just fine. However the keyboard function keys do not. I've tried using PuTTY, gtkterm, and Moserial and all 3 of those terminal programs yield different and invalid function key responses with my external device. Those programs provide no capability to specifically customize the function keys. Is there any such available serial-comm program out there that I could use that does provide such keyboard customization?

---

### Post by The Cog on 2018-12-30
It might be possible with **minicom** - the only serial program I have ever used on Linux.
[https://www.irongeek.com/i.php?page=backtrack-3-man/minicom](https://www.irongeek.com/i.php?page=backtrack-3-man/minicom)

---

### Post by n2te on 2018-12-30
Thanks. Will try minicom.

---

### Post by him610 on 2018-12-30
What about gkermit?
G-Kermit is a GPL'd kermit package. It offers medium-independent terminal
session and file transfer. The non-free package ckermit adds connection
establishment, character-set translation and scripting features.

---

