---
title: "Error 1962: no operating system found"
date: 2022-09-13
forum: General Help
---

### Post by dayroxy on 2022-09-13
Hello Guys, ive installed ubuntu server 22.04 on my old lenovo pc but i keep on getting error 1962 no operating system found im choosing the correct boot option the only hdd ive got 
Also i tried boot options legacy and also tried uefi 
And in the bios there is no secure boot or csm to turn off i dont have that kinda of options on my bios in security tab how can i fix the issue?

---

### Post by jeremy31 on 2022-09-13
See if the HDD is using GPT instead of ms dos partitioning  wirh ```
sudo parted -l
```
Some older machines can't use GPT

---

### Post by dayroxy on 2022-09-13
Where can i type the command?
i cant access the OS, i only get to the installations and when i finish it will restart and get the error, also i tried pressing C when choosing the installation to open the terminal but i get parted command not found

---

### Post by jeremy31 on 2022-09-13
Boot any live ISO on USB and run the command

---

### Post by oldfred on 2022-09-13
Another older Lenovo
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

 Do you have latest UEFI from Lenovo?
Error seems to be related to not finding a Windows UEFI boot entry. 
Solution above was to create a Windows (description only) boot entry that actually boots shimx64.efi, to boot Ubuntu.

---

