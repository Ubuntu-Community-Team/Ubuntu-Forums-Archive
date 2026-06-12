---
title: "Booting Issue"
date: 2013-03-28
forum: General Help
---

### Post by PatchWarfare on 2013-03-28
I am attempting to do a live boot via USB of ubuntu version 12.10, I have used Unetbootin to create the boot-able media and it worked on a separate computer. 
The issue is that after the purple loading screen with the bubbles filling up, the load pauses and I get a blank screen.  I have tried to hit ctrl alt F1, and nothing happens.

The issue is on a computer running:
Gigabyte 990FXA-UD3                      -mobo
AMD 8350                                      -CPU
ASUS HD7770                                 -GPU
8Gb 1600MHz                                 -RAM
120Gb OCZ SSD (Agility 3)                -HDD

---

### Post by PatchWarfare on 2013-03-28
does anyone have any ideas?

---

### Post by grahammechanical on 2013-03-28
At the very first purple screen press Enter. Then select your language (default is English) and press Enter again. At the Try - Install screen press F6. You will see a small menu with options. Try some of them. Start with nomodeset. Select an option and press Enter and then Esc to get back to the Try - Install screen where you can select Try Ubuntu. You may need to try a combination of F6 options to get a Live Session working.

Regards.

---

### Post by PatchWarfare on 2013-03-28
no purple screen appears, I go straight to a black screen that is GNU Grub 2.something and it gives me the options try, install, install OEM, and another, I've tried entering command line by pressing c, going to to the previous page by pressing escape and pressing e to edit boot options but all result in a black screen

---

### Post by PatchWarfare on 2013-03-28
EDIT:  I am now able to get to the unetbootin window by changing a bios setting and manually choosing to boot from the USB generically (without UEFI).  however I still run into the issue of the screen going blank after the boot sequence of ubuntu.

---

### Post by PatchWarfare on 2013-03-28
SOLVED boot, used 12.04 and it booted no problem, guess I'll have to avoid using 12.10.  Anyway, now that I have booted into 12.04, I cannot use my rear 2.0 ports, the USB 3.0 ports are the only ones working.  Any fixes for that?

---

