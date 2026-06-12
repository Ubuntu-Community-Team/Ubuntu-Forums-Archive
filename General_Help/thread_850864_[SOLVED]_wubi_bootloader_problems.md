---
title: "[SOLVED] wubi bootloader problems"
date: 2008-07-06
forum: General Help
---

### Post by steve needs help on 2008-07-06
i installed ubuntu yesterday using wubi 1.8.04.1 on 
xp sp3 v3264 software on my d: drive . the loading seemed to go well. when i rebooted the screen read select windows or ubuntu .. use arrow keys. when i tried to select ubuntu the arrow key wouldn't highlight ubuntu (as if it wasn't even there). could someone please offer advice. I am not an advanced computer user so a relatively simple explanation would be appreciated. 

my apologies if this issue has been discussed on another thread but i couldn't find this specific problem. thanks for any help.

---

### Post by ago on 2008-07-06
It means that your Bios/Windows bootloader does not support your keyboard
Not really a Wubi problem as at that stage you are in ntldr, and you would have the same problem with any other dual boot such as XP/VISTA.

In some cases there are settings (usb) you can change in the bios, otherwise you will have to use a different keyboard.

---

### Post by steve needs help on 2008-07-06
thanks for your prompt reply. i am using a dinovo edge keyboard. i also tried a usb plug in keyboard. neither of these worked. any suggestions as to what program area i should look and what i should look for to enable my keyboard

---

### Post by steve needs help on 2008-07-07
once again thanks for your help. i used an old ps2 keyboard to get me through the boot process. my dinovo keyboard was then fine operating within ubuntu. cheers

---

### Post by digitalggs on 2008-07-08
In most BIOS you can enable USB support. So the BIOS can work the USB hub(s) without an OS (drivers). To enter BIOS on most systems you hit F2 or DELETE key when you first turn the computer on (should say on screen which it is). 

  POke around the settings (be careful not to change anything other that what your there for). It will be usually under 'INtergrated..' or 'Onboard..' something like that. Look for something that says USB support or BIOS USB. If it is a manufactured PC (Dell, Gateway, HP etc.) Check with your support service or thier support site. It is not an uncommon request.

---

