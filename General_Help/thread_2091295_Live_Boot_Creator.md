---
title: "Live Boot Creator"
date: 2012-12-04
forum: General Help
---

### Post by Synoc on 2012-12-04
I am trying to make a liveboot usb  of Linux Mint. I used the startup disk creator and it made an additional (unmountable) filesystem on my hard drive (Linux Mint MATE 64-bit) anyone know what it is and what it's for? I am trying to make a live boot, similar to a live boot CD but on a USB so it is read/write, not just read. What is the other file system for on my hard drive?

Additionally, It won't boot from the USB drive. I choose Start Linux mint from the boot menu the screen goes grey for a moment, then nothing. The monitor is on (and getting a signal), but it will go no further than that. I do an integrity check and it shows 4 file errors, but I can't see seem as quickly as they pass by. if I use the same ISO for virtually, it works fine. any ideas what the problem is?

---

### Post by orb9220 on 2012-12-04
*"Additionally, It won't boot from the USB drive."*

Seems the main problem to solve. Do you have boot from usb in bios option? Select it as first boot device. And it's not booting from there?

As you can't boot it from within windows as far as I understand how it works.
So solving why it won't boot up from cold start would be the issue. Either not having the option in bios or something not right on usb for it to boot 1st from bios.
.

---

