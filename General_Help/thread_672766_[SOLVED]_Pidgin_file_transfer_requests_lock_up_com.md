---
title: "[SOLVED] Pidgin file transfer requests lock up computer"
date: 2008-01-19
forum: General Help
---

### Post by nitromanrc on 2008-01-19
Every time I receive a file transfer request in pidgin, when i try to focus that window, my computer locks up...I can move the mouse, but I can't click anything, can't use the keyboard, music keeps playing, but i cant really do anything without a reboot (the nasty way...w/ the button)
I have no idea why this is happening, but its very annoying 

Specs: AMD Athlon x2 3800
GPU: Onboard Nvidia Geforce 6100 (driver 169.07)
Mobo: Biostar Geforce 6100-m9
1 gb ram
brand new hdd...not the problem


Thanks in advance

o yeah...im good w/ a terminal...and i've been using ubuntu for a while now so complete beginner talk  isn't necessary

---

### Post by diaa on 2008-01-26
I'm not sure how to solve this problem but I wanted to tell you that you can restart the PC gracefully to avoid any data loss instead of a hard reboot.
Use Ctrl+Alt+F1 to switch to *tty1* then login and run the command ```
shutdown -h
```to turnoff the PC
or ```
shutdown -r
```to restart the PC.
Also you may run
```
pkill pidgin
```To kill pidgin and avoid the restart altogether

-- 
Diaa Sami

---

### Post by nitromanrc on 2008-01-28
I can't even use ctrl+alt+F1...it does nothing when its locked up like that...

---

### Post by diaa on 2008-01-28
May be you should try the [SysReq solution]("http://ubuntuforums.org/showthread.php?t=617349") as the last resort, it's still better than the power/reset keys.

---

### Post by nitromanrc on 2008-01-29
Weird...i had my friend send me some file transfer requests today and i couldn't replicate the situation..although the day of the post, it happened many times, every time i got a request...so i just told my friends not to send me stuff over aim..rather use email..but i guess since i can't replicate it i can just forget about it till it happens again....thanks anyways guys...

O yeah...those SysRq keys...i had no idea about that...thanks alot thats very useful for when trying out new things (haha buggy xserver drivers especially)

---

