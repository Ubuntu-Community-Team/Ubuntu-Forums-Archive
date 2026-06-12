---
title: "Lubuntu 16.04.3 freezes/hangs randomly"
date: 2018-01-08
forum: General Help
---

### Post by doc-1 on 2018-01-08
I am using Lubuntu 16.04.3 (64 bit, up to date) and it is freezing seemingly randomly. Previously I was using Lubuntu 15.10 (32 bit) and it wasn't freezing. 
 
I clean installed the 16.04.3 version, but my /home folder originates from the 15.10 version. 
 
Can you please help me troubleshoot this issue? 
 
 
Software: 
    - Audacity from external PPA (the Audacity team suggested it) 
    - LibreOffice (I downloaded the .deb files from their website) 
    - wine-stable from wineHQ 
    - a 32-bit spectrogram program running with Wine 
    - Intel graphics update tool and the drivers inside that (but the freezing started before I installed these) 
 
 
Hardware:
    Acer ES1-131 notebook (Intel Pentium N3700 Braswell CPU and HD Graphics 405)
    - USB hub (but the freezing started before it)
    - external keyboard, mouse

edit:
I forgot to add:
The '/var/crash' folder is empty.
Pressing Ctrl+Alt+Backspace does nothing.
Pressing Alt+Sysrq+R E I S U B does nothing.
            
When the freeze occurs, the screen stays on and the computer hangs.

edit2:
I tried applying the c-state workaround for the infamous Bay Trail CPU bug, as described here, but it didn't solve the problem:
[https://askubuntu.com/questions/803640/system-freezes-completely-with-intel-bay-trail](https://askubuntu.com/questions/803640/system-freezes-completely-with-intel-bay-trail)
I know my CPU is not Bay Trail.


On another thread I found that a person with the same CPU as mine installed Xubuntu 17.10, and it solved the problem.
[https://ubuntuforums.org/showthread.php?t=2367549&page=4](https://ubuntuforums.org/showthread.php?t=2367549&page=4)

Should I update to Lubuntu 17.10?


edit3:
I enabled Intel microcode from the update selection GUI.
It didn't provide a fix.

On a note, the output of
> $ dmesg | grep microcode
is
> [    2.850605] microcode: sig=0x406c3, pf=0x1, revision=0x35e
[    2.850685] microcode: Microcode Update Driver: v2.2.


Does this mean that the microcode was already up to date, or does it mean that the microcode is not updated?

---

### Post by doc-1 on 2018-01-10
Bump!

---

