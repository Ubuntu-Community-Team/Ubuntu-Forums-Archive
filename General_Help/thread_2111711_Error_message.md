---
title: "Error message"
date: 2013-02-02
forum: General Help
---

### Post by aweshucks78 on 2013-02-02
end_ request:  I/O error, dev sda,  sector 103829. 
How do I fix this please help

---

### Post by Bashing-om on 2013-02-02
aweshucks78; Hi !
File corruption ?
Boot ubuntu to the grub menu, choose "recovery mode" -> choose "fsck" to check/repair the file system; upon completion -> "resume normal boot" -> login -> Reboot.

Hard disk failing ?

What does the "disk utility" report for the health of the hard disk ?

[INDENT][INDENT]hth

[/INDENT][/INDENT]

---

### Post by aweshucks78 on 2013-02-02
> **Bashing-om said:**
> aweshucks78; Hi !
File corruption ?
Boot ubuntu to the grub menu, choose "recovery mode" -> choose "fsck" to check/repair the file system; upon completion -> "resume normal boot" -> login -> Reboot.

Hard disk failing ?

What does the "disk utility" report for the health of the hard disk ?

[INDENT][INDENT]hth

[/INDENT][/INDENT]

recordfail
gfxmode $Linux_ gfx_mode 
insmod  gzio
insmod part_ msdos 
insmod ext2 

plus I don't have resume normal boot option in grub menu. 
further more if I chose recovery  mode how long should it take? 
it won't even let me run sudo codes, and it's on a netbook so I don't have a CD disk. 
thanks for response I hope your having a wnderful groundhog day

---

### Post by Bashing-om on 2013-02-02
aweshucks78;

The system can not find the boot code. Still try to repair the file system as advised earlier.

At the grub menu choose "recovery mode"
this will activate the recovery console with several options, the one we are interested in is "fsck". Arrow down in this menu to "fsck" and press the enter key. Will begin the file system check process. Upon competion of the check, arrow up to the first option "resume normal boot" press enter.

If all is well at this time will go to the GUI login, graphics state will have a lower resolution, that's OK. Login to your system. From the desktop reboot.

If this method is not a success, will have to use grub's command line or use an external live medium to access the system and tell grub where/how to set the boot code.
[INDENT][INDENT]hth

[/INDENT][/INDENT]

---

### Post by aweshucks78 on 2013-02-02
cannot open /var /log/username /2 read- only  file system 

My trap (core dumped )               fail


I'm in grub editenv now 

guess through code is the second option you had that we could try

thx again

---

### Post by Bashing-om on 2013-02-02
aweshucks78; 

Your last reply gives cause for concern that the file system is badly damaged.
a) read only -> file system is protecting it's self to prevent additional damage;
b) core dumped -> system is experiencing non recoverable errors allowing debugging the code to find the fault. That is beyond my ability.

Perhaps others with greater knowledge will advise, but looking at the probability of (re) installing.

[INDENT][INDENT]wait a bit and see

[/INDENT][/INDENT]

---

