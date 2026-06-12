---
title: "Help on two os systems"
date: 2008-05-06
forum: General Help
---

### Post by XDarkzAngelX on 2008-05-06
I had windows xp installed than installed ubuntu is there a way i can have windows xp load automatically than me open ubuntu or do i have to chose from the list on startup?

---

### Post by kpkeerthi on 2008-05-06
Yes it can be done. Can you post your /boot/grub/menu.lst file content here?

---

### Post by XDarkzAngelX on 2008-05-06
#This file is modified at runtime by bootmenu.nsh

debug off
hiddenmenu 
timeout		5
default		0

title Start installer in normal mode
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/installation.iso automatic-ubiquity noprompt quiet splash boot=casper ro debian-installer/locale=en_US.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --  
initrd /ubuntu/install/boot/initrd.gz
boot

title Start installer in safe graphic mode (only if you have display problems)
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/installation.iso automatic-ubiquity noprompt quiet xforcevesa boot=casper ro debian-installer/locale=en_US.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --  
initrd /ubuntu/install/boot/initrd.gz
boot

title Start installer with ACPI workarounds (only if you have ACPI problems)
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/installation.iso automatic-ubiquity noprompt quiet boot=casper ro debian-installer/locale=en_US.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --   acpi=off noapic nolapic
initrd /ubuntu/install/boot/initrd.gz
boot

title Start installer in verbose mode
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/installation.iso automatic-ubiquity noprompt debug debug-ubiquity boot=casper ro debian-installer/locale=en_US.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --  
initrd /ubuntu/install/boot/initrd.gz
boot

title Read-Only Demo (Live CD Desktop)
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz iso-scan/filename=/ubuntu/install/installation.iso quiet splash boot=casper ro debian-installer/locale=en_US.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --  
initrd /ubuntu/install/boot/initrd.gz
boot

---

### Post by ejay563 on 2008-05-06
This file looks like you are running from the live cd. Are you? If not... wierd... but here's what you would do. 

1. open terminal
2. type sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.back
3. then sudo gedit /boot/grub/menu.lst
4. scroll down near the bottom and look for where your windows entry is. Notice how each entry is separated, then count to see whicn number down your windows entry is. Remember that number
5. scroll back up near the top, and change "default 0" to "default X"; x being the number of your windows entry -1 (since it starts counting from 0). 

This should have you booting into windows automatically.

---

### Post by XDarkzAngelX on 2008-05-06
yea im not runnin live so i guess it may be weird than lol

---

### Post by XDarkzAngelX on 2008-05-06
um i dont understand most of that so can someone help

---

### Post by wford002 on 2008-05-06
I use the "start up manager" program to change this. Just go to add/remove under applications and search for start up manager. it's really straight forward.

---

### Post by XDarkzAngelX on 2008-05-06
no of these worked why idk

---

### Post by kpkeerthi on 2008-05-07
> **XDarkzAngelX said:**
> #This file is modified at runtime by bootmenu.nsh

debug off
hiddenmenu 
timeout		5
default		0

title Start installer in normal mode
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/installation.iso automatic-ubiquity noprompt quiet splash boot=casper ro debian-installer/locale=en_US.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --  
initrd /ubuntu/install/boot/initrd.gz
boot

<--- [removed] --->
...


You seem to have posted the boot menu entry of Live CD. Apparently there is no Windows XP listed in here. So it cannot be made to boot by default. 

Does your boot menu has Windows XP listed in it? Shutdown your Live CD session, remove the CD from tray, boot off ubuntu installed in your hard drive and post back the menu.lst content.

---

