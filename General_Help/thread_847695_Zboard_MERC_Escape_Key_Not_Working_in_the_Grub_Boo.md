---
title: "Zboard MERC Escape Key Not Working in the Grub Bootloader"
date: 2008-07-02
forum: General Help
---

### Post by Gargleman on 2008-07-02
When I boot up my machine and I attempt to hit escape so I can go to my bootloader and go to my windows xp partition, the escape button on my zboard Merc does not respond. The keyboard however, works fine once I am in Ubuntu and Windows

---

### Post by soccerboy on 2008-07-02
usb keyboard, built-in or ps/2?

---

### Post by Gargleman on 2008-07-02
sorry, its a USB keyboard.

---

### Post by soccerboy on 2008-07-02
did this happen before or did it start recently?  if it has always been like this, some bios do not recognize usb keyboards or have an option to enable usb support.  You might try using a ps/2 keyboard to see if it fixes this and then try to find the option in your bios.

---

### Post by Gargleman on 2008-07-02
it happened since the start, the keyboard works fine once I am in an OS though. I need to use a ps/2 keyboard when I want to go into windows though.

---

### Post by soccerboy on 2008-07-02
see if you can find something in your bios that states to enable usb for the bios.
By the way, can you enter bios setup with the usb keyboard?

---

### Post by Gargleman on 2008-07-02
yeah I can use the usb keyboard to get into the bios, just chcked

---

### Post by soccerboy on 2008-07-02
that's strange.  i don't know the problem.  Someone more skilled may be able to help.  sorry.
EDIT: Sounds like it may have been a problem in grub installation.  Did you get any errors when you installed ubuntu?

---

### Post by Gargleman on 2008-07-02
no apology needed my friend, your advice helped! I went into the bios and it turns out USB keyboard support was disabled. Enabled it and now it works perfectly. Thanks.

---

### Post by soccerboy on 2008-07-02
glad i could help

---

