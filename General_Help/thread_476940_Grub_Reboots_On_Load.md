---
title: "Grub Reboots On Load"
date: 2007-06-17
forum: General Help
---

### Post by NTITech on 2007-06-17
For some reason Grub randomly decides to reboot.  It'll display "loading stage 1.5" then reboot.  Super Grub Disc also reboots when I try to restore Grub and when I try to load my linux with it.  The only way to fix my problem is to load a live cd and fix it through the terminal (using sudo grub...).  Why is this happening?  Note: I have Vista installed on the 1st partition and Kubuntu Feisty on the 2nd.

---

### Post by smoker on 2007-06-17
you could maybe try a complete reinstall of grub, have a look at this link:
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

best of luck

---

### Post by binarybird on 2007-06-17
My suspicion is the Microsoft Dynamic Disk feature is writing data out to the MBR when you are inside Vista (this happens on XP as well). This causes issues with Grub when it hits stage1_5. Data is missing...it reboots. Vicious cycle over and over. Wash, rinse repeat so to speak. You fix it with your live CD and the next time you boot into XP/Vista...it bumps your MBR again. 

To fix this...

- Boot into your live CD and repair the grub installation
- When you have repaired grub and it boots for the first time enter Ubuntu
- cd into your /boot/grub directory
- delete any file with 1_5 (rm *1_5)
- reinstall grub again from within ubuntu

Once it writes out to the MBR you should be fine. 

Hope this helped...
I'd insert my "works on my machine" certified sticker here if I had it with me :)

---

