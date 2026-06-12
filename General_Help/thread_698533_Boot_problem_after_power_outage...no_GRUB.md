---
title: "Boot problem after power outage...no GRUB?"
date: 2008-02-16
forum: General Help
---

### Post by Unstuck on 2008-02-16
Last night we had two power outages within about 45 seconds.  The computer is protected by a surge protector, but since then it will not boot to the grub loader.  After turning the computer on it shows info about the video card and the HP splash screen then the screen goes black and the cursor flashes in the upper left hand corner.  I cannot choose a kernel to load or enter into terminal screens.  The cursor just flashes...I think it's mocking me.

The comp runs 7.10

---

### Post by dayanandasaraswati on 2008-02-16
Think your MBR is erased. Follow this link and you'll get back your mbr in no time.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Unstuck on 2008-02-16
The Live CD does not load.  :(

---

### Post by dayanandasaraswati on 2008-02-16
Can you eloborate on it.. What error do you get while loading live cd

---

### Post by Unstuck on 2008-02-16
I put the Live CD in the drive, rebooted, and the same thing occurred: vid card info, splash screen, flashing cursor.  No error messages or indication it recognizes a CD is in the drive.

---

### Post by dayanandasaraswati on 2008-02-16
May be that the power outage has damaged your hardware. I think your bios is not allowing your system to boot. This could result when you have some hardware failure. Check if you are hearing any beep sounds while booting. If so count the number of beeps and google up for a solution. If you don get any beep sounds, go to bios and check if you have some option called Quick boot. Try disabling it. This would make bios prompt you in the event of any error.  Browse through all menus and try to enable some options which could display the output of the Hardware test which bios does. Examine the hardware test results for some irregularities.

---

### Post by Unstuck on 2008-02-16
Thank you for your help, dayanandasaraswati.

For some reason, I wasn't able to enter BIOS until I turned off the comp and unplug it for a few minutes.  After turning it back on, I followed your advice and disabled Quick Boot, and I was able to get to GRUB loader and load 7.10.  I have no idea what happened or how the problem was fixed, but everything seems to work now.

---

### Post by dayanandasaraswati on 2008-02-16
No probs..Enjoy...

---

