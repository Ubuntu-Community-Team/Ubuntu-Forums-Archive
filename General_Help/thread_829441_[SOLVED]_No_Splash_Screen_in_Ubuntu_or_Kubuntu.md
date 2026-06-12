---
title: "[SOLVED] No Splash Screen in Ubuntu or Kubuntu"
date: 2008-06-14
forum: General Help
---

### Post by omega17 on 2008-06-14
When I boot i get all of the system text:
```
Loading Bluetooth Manager...        [ OK ]
```
I would like to see the Ubuntu or Kubuntu Splash Screen.


P.S. Dual booting Ubuntu, Kubuntu 2 HD's, and they both show up as Ubuntu 8.04, Can i make one Kubuntu 8.04

---

### Post by avtolle on 2008-06-14
I think somehow, "quiet splash" is not in the boot line, so (I think F6 gets you there) you need to add it or, if it says "no splash", replace the no splash with quiet splash.

As to your second question, K/Ubuntu is the same under the desktop installed. Not sure what you want to do.

---

### Post by VMC on 2008-06-14
> **omega17 said:**
> When I boot i get all of the system text:
```
Loading Bluetooth Manager...        [ OK ]
```
I would like to see the Ubuntu or Kubuntu Splash Screen.


P.S. Dual booting Ubuntu, Kubuntu 2 HD's, and they both show up as Ubuntu 8.04, Can i make one Kubuntu 8.04

Startup Manager is a great tool to help with this. Display output of 
```
cat /boot/grub/menu.lst
``` Look for title, then go down to kernel and what does the end of the line show?

 Mine is this  'splash vga=773'. It depends on your ghaphics card. Mine can only support 1024x768

---

### Post by omega17 on 2008-06-14
I am kinda confused when i boot. can i make one say Kubuntu and one say ubuntu so i done get confused.

---

### Post by VMC on 2008-06-14
> **omega17 said:**
> I am kinda confused when i boot. can i make one say Kubuntu and one say ubuntu so i done get confused.

Edit: ```
sudo  nano /boot/grub/menu.lst
```  Find "title". To the right is the where the name appears. You can change that line to what you want.

---

