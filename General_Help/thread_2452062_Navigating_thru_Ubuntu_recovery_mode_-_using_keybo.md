---
title: "Navigating thru Ubuntu recovery mode - using keyboard ??"
date: 2020-10-15
forum: General Help
---

### Post by helen314 on 2020-10-15
[https://www.freecodecamp.org/news/the-ubuntu-recovery-menu-demystifying-linux-system-recovery/](https://www.freecodecamp.org/news/the-ubuntu-recovery-menu-demystifying-linux-system-recovery/)

After scanning thru the above link I am still  not sure how to navigate / select item from the non-gui  recovery menu.
I was guessing it should be done by keyboard upper / lower arrows = but it does not do. 
I usually get strange characters and if I am lucky iI can get to next menu by pushing "Enter". 
I am using both "plug in" and wireless keyboard. with same results. 
Not really sure how wireless keyboard functions in "recovery mode " anyway.

---

### Post by TheFu on 2020-10-15
The arrow keys should work.

My wireless keyboard (not bluetooth) works fine, but that's because the OS only sees a typical USB HID keyboard.
I've never seen the issue described.  Only 1 thing comes to mind to check in the BIOS - there should be a setting for USB "legacy mode", enable that. 

BTW, if my /boot/ partition had that many old kernels, I'd have run out of room for any kernel updates 6 months ago.  I think about 5 kernels is all my /boot/ can hold. Any more than that is "out of space" error and a world of APT pain will happen.

Of course, if the install doesn't have a separate /boot/ partition, then having 500 kernels is probably fine.  Generally, I keep 2-3 kernels, total. This avoid nasty APT issues that aren't fun to correct.

---

### Post by helen314 on 2020-10-15
My wireless keyboard (not bluetooth) works fine, but that's because the OS only sees a typical USB HID keyboard.
I've never seen the issue described.  Only 1 thing comes to mind to  check in the BIOS - there should be a setting for USB "legacy mode",  enable that. 

I have been concentrating on recovering my Qt program and the "USB legacy" is still an issue. 
Today I finally managed to load the QT program. Of course my PC is a huge mess , somehow I have "new" grub file with entries to about 7 Ubuntu OS. 

I need to update my UEFI and that allegedly  includes "improvement " in handling USB.
I have not look at UEFI setup recently, but I accidentally  "disabled legacy  USB" once and lost my USB mouse in the process. 

However, since I got my Qt program back I will put this keyboard issue in recovery mode on back burner for now.

After your comment I better delete any unnecessary OS. 
Appreciate your help.

---

### Post by TheFu on 2020-10-15
Grub entries are just found kernels, not necessarily entire OSes.

---

