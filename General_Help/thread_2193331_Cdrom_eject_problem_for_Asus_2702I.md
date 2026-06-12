---
title: "Cdrom eject problem for Asus 2702I"
date: 2013-12-12
forum: General Help
---

### Post by oleg3 on 2013-12-12
If I push eject button the cdrom does not eject. 
dmesg gives
[63438.665110] asus_wmi: Unknown key b1 pressed
[63442.375238] asus_wmi: Unknown key b1 pressed



if i run 
root@oleg-ET2702I:/etc# showkey 
kb mode was ?UNKNOWN? 
[ if you are trying this under X, it might not work 
since the X server is also reading /dev/console ] 

press any key (program terminates 10s after last keypress)... 
keycode 240 press 
keycode 240 release 
keycode 240 press 
keycode 240 release 
Please help to solve this problem
Oleg

---

### Post by mörgæs on 2013-12-13
Have you tried the **eject** command?

---

### Post by oleg3 on 2013-12-15
If there is a CD then if I run eject command it opens. But if there is no CD so it does not open.
Oleg

---

### Post by oleg3 on 2013-12-18
[h=2]Cdrom eject problem for Asus 2702I[/h] 		 				 					 					 				 				 		 			 				[INDENT] 					If I push eject button the cdrom does not eject. 
dmesg gives
[63438.665110] asus_wmi: Unknown key b1 pressed
[63442.375238] asus_wmi: Unknown key b1 pressed



if i run 
root@oleg-ET2702I:/etc# showkey 
kb mode was ?UNKNOWN? 
[ if you are trying this under X, it might not work 
since the X server is also reading /dev/console ] 

press any key (program terminates 10s after last keypress)... 
keycode 240 press 
keycode 240 release 
keycode 240 press 
keycode 240 release 
Please help to solve this problem
Oleg 				[/INDENT]

---

### Post by Impavidus on 2013-12-18
Maybe you can eject using the **eject** command. I unmounted first, but that may not be necessary. On my laptop using the eject button works, but that may be hardware dependent.

---

### Post by mörgæs on 2013-12-18
Threads merged. 

If you don't receive an answer (and sorry for not being able to do that) it's better to bump the thread after more than 24 hours than opening an new one.

---

### Post by oleg3 on 2013-12-19
> **Impavidus said:**
> Maybe you can eject using the **eject** command. I unmounted first, but that may not be necessary. On my laptop using the eject button works, but that may be hardware dependent.

The problem is if there no CD then you can not unmount and use eject command. Eject works if there is a disk.

---

