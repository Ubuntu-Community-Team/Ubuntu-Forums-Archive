---
title: "hd failure ... grub"
date: 2008-01-25
forum: General Help
---

### Post by rbateai on 2008-01-25
Greetings
I have Ubuntu on a dual boot with XP .. Ubuntu is on a different HD than XP. Ubuntu drive is failing so on boot I get a grub error and it hangs. How do I change this? Would like to uninstall grub from the MBR, then I can replace the failing drive and reinstall Ubuntu. 
Any help greatly appreciated.
Thanks!

---

### Post by King Cotton on 2008-01-25
The same thing  happened to me. Easy fix though.

1. With the computer powered off, disconnect the failing hard drive.
2. Turn on the computer and place an XP disc in the CD/DVD drive.
3. Boot to the XP disc and wait for it to load.
4. You will be given a list of options, select "Recovery"
5. At the command prompt, type "fixboot" then press Enter, it will ask you if you are sure, type "y" then press Enter.
6. Next, type "fixmbr" then press Enter, it will ask you if you are sure, type "y" then press Enter.
7. Type "reboot", the computer will restart and boot up into M$ Windows.


Let me know if you have any problems.

---

### Post by rbateai on 2008-01-25
Thank You kindly. Will let you know.

---

