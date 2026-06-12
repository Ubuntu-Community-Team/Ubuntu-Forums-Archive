---
title: "Ubuntu Installation Freezes (Custom Gaming Laptop)"
date: 2015-11-19
forum: General Help
---

### Post by Benjamin_Brown on 2015-11-19
Hello all,

I am trying to install Ubuntu 15.10 on my Cyber Power PC Gaming Laptop as a dual boot with Windows 10. I have refind installed, and whenever I try to run the Ubuntu Installer it freezes after about a minute or so (the mouse doesn't move, not keyboard input, etc), and the one time that I did manage to install the OS it would freeze as such every 5 minutes or so. I have looked everywhere, and I suspect the graphics drives to be at fault, but I cannot for the life of me find the solution to this problem. My specs are as follows:
Intel i7 2.7GHz Processor
NVidia GeForce 970M Graphics Card
(assumingly) MSI motherboard (the power supply is MSI, and MSI would make sense here)
16gb 1600MHz RAM
250GB M.2 SSD
2TB HDD

Thanks in advance

---

### Post by Geoffrey_Arndt on 2015-11-20
Likely video system is causing issue  . . . due to no nvidia driver installed by default in standard Ubuntu install process.    Some proprietary drivers will be installed during install steps IF proper checkbox's enabled at setup screen (e.g., install 3rd party software) BUT, what is likely required is to use a boot-up parameter of "nomodeset" . . . . . I have to run now, but if you do a standard google search for "ubuntu nomodeset" you'll find plenty of specific tutorial links back to this forum or other great forum sites like "askUbuntu" . . . good luck.

(note, if you do boot up into a lower res version of ubuntu - - FIRST thing to do is goto "system settings>software & updates>additional drivers tab.    Let the system scan for a minute, and select the proper nvidia driver to initiate download/install.

EDIT:   found one of my notes files about nomodeset:

 To enable boot via "nomodeset" grub option" 
   

[LIST]
[*]Boot the machine and at the grub menu highlight the kernel you want to use and click 'e' to edit.
[/LIST]
    

[LIST]
[*]Find the line that ends in 'quiet splash' and after a space, add 'nomodeset'.   The end of the line should look like this:
[/LIST]
    quiet splash nomodeset 
   

[LIST]
[*]Follow the instructions at the bottom of that screen to save changes and continue
[/LIST]

---

### Post by VMC on 2015-11-20
You can also try adding 'nouveau.noaccel=1' at the end of the 'linux' line instead of 'nomodeset'.

---

