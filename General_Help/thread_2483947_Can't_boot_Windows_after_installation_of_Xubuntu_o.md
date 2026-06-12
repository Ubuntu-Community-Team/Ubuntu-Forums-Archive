---
title: "Can't boot Windows after installation of Xubuntu on DELL PC"
date: 2023-02-13
forum: General Help
---

### Post by msauer75 on 2023-02-13
HI,

I got my new DELL Precision 3660 PC. After the setup of Windows is completed (upgrade to Windows 11) I split the M.2 into to parts and installed Xubuntu on the second half. (I do this on my own build PC). 
Now I want to start Windows, but I doesn't. Windows will try to repair the installation without any success. I can try again or shutdown the PC. This will comes every time I select Windows in the grub menu. 
Is there a solution for this problem? What can I do to solve it?

In Xubuntu I also can't access the NTFS partitions of my other drives. I will be prompted for a key, but I don't have a key. 

Is this a UEFI Problem? What can I do? Why I don't have these problems in my own build pc?

Thank you for your help-
BR
martin

---

### Post by dragonfly41 on 2023-02-13
As another Dell user .. Try installing ReFind in your Windows.

[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

Then in your BIOS (F2 or F10 to view) select Refind as your boot option.

[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
 
You can always go back  to your default boot option.

There is also Boot Repair in Ubuntu to try.

---

