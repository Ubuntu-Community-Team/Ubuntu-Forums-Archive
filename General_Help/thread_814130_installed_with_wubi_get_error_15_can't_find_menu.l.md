---
title: "installed with wubi: get error 15 can't find menu.lst"
date: 2008-05-31
forum: General Help
---

### Post by thechilipepper0 on 2008-05-31
alright.
I installed hardy with wubi, and then it said to reboot the computer to finish installation.

But then it comes to the OS selection screen. when i select ubuntu i get something like:

Error 15: find /wubi/install/boot/grub/menu.lst

all the information I've found is outdated. i found one that said grub might have trouble with multiple hard drive configurations (I have two on this comp), and the fix said to alter menu.lst. However, menu.lst apparently has been update since that fix.

also, the os selection screen takes too long. how do i change the timeout?

---

### Post by Cookie1456 on 2008-05-31
So you have two hard drives? If you ubuntu is on another drive seperate from the boot loader (i.e. the windows drive) then try this.

1.Restart computer and select Ubuntu
2.Press 'Esc' and highlight ubuntu and press 'E'
3.Edit the first line from (hd0,0)/ubuntu/ to (hd1,0)/ubuntu/
4.Press enter then press b to boot
5.It should work

If it works go under (on windows) D:\ubuntu\disks\boot\grub (or whatever the drive name where you installed it) there is a file menu.lst, back it up and edit it, use the replace function to replace (hd0,0)/ubuntu with (hd1,0)/ubuntu and it should work

---

