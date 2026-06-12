---
title: "Boots into unsupported screen resolution.."
date: 2017-11-05
forum: General Help
---

### Post by joe.snider on 2017-11-05
Found my old Dell Mini 9 (Inspiron 910) and wanted to see how it handled lubuntu. 

Created a USB boot drive. Booted to it. Graphics are normal, readable and uses correct screen resolution.

Installed to internal drive, rebooted and I get a partial desktop to the right of the screen but black/garbled text on the remainder of the left side of the screen. 

If I plug in an external VGA monitor everything works as it should.  I can then turn off the external monitor and use the builtin lcd at 1024x600 - which lubuntu detects and uses. Apply and save settings then upon reboot it reverts back to the original issue.

---

### Post by Kris_M on 2017-11-06
change 3rd line of grub on bootup to 
grub_gfxmode=1920x1080 (change to the resolution you want)

Also might try add nomodeset to linux command in grub boot.

Since you're editing grub on bootup these would be temporary changes so no worry if it doesn't work.

---

### Post by joe.snider on 2017-11-06
That did the trick.. Now I need to make it stay that way.

---

### Post by Kris_M on 2017-11-06
excellent! - I use grub customizer to make changes...  I don't know how to do it the other way, though I have been told... :)

---

