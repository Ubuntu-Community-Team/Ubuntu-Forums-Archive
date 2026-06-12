---
title: "Installing 18.04 as dual boot, need to get into kernel boot options to act. nomodeset"
date: 2019-04-01
forum: General Help
---

### Post by swarup on 2019-04-01
I booted up to the 18.04 install usb to install 18.04 as a dual boot. When 18.04 booted up from the installation usb, I got a screen filled with multicolored distortion, rather than the desktop. I think what I need to do is get into kernel options and activate nomodeset. This I had done earlier with 14.04 installation usb, and it worked perfectly. But I have forgotten how to open the screen where I can select this. Please kindly see below, the directions which I used in the past for this. But I am not getting the purple screen with a keyboard logo as described below, in the current computer.

> How to enable kernel options on the livecd (before install)

If you boot ubuntu from a livecd (or USB stick), right after the bios splash screen you will get a purple screen with a keyboard logo at the bottom. Press any key at that moment to access a menu. Select your language with the arrow keys, press enter and you will see a menu. If you press the F6 key, a menu at the bottom will open allowing you to set kernel options with the space bar or enter key. You can close the menu with escape key and resume booting by selecting the option &#8220;try ubuntu without installing&#8221; (please note that session does allow you to install ubuntu once you found the kernel options cured your problem).

---

### Post by swarup on 2019-04-01
I got the solution. Here is how to activate nomodeset for anyone that needs it:

> Hover over the option &#8220;Try Ubuntu without installing&#8221;.
Press e.
Add nomodeset after the words quiet splash. Then F10 to save changes and boot. 

Worked great!

---

