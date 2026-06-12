---
title: "Reboot to windows"
date: 2007-03-03
forum: General Help
---

### Post by CuBone on 2007-03-03
Is there a way to reboot to windows? Im using grub to dualboot ubuntu + winxp. If I'm in ubuntu Id like the option to reboot to windows withouth having to sit by the computer and select the proper os in grub.
When I'm in win and need ubuntu I'll just reboot the computer. Since ubuntu is the auto choice in grub that way is no problem.

---

### Post by invalid on 2007-03-03
I can only see one way to make this possible, but no idea how it would be done.

What would need to take place, is a mofication to your default boot value in /boot/grub/menu.lst whenever you click this option.

I have never heard of such a tool, but it would be an interesting feature to have for dual boot users.

---

### Post by houstonbofh on 2007-03-03
You will need to edit /boot/grub/menu.lst and have two.  As root, you will need to make a menu.lst.linx and a menu.lst.win and you will need a couple of scripts.  One script (windows) will be
```
rm /boot/grub/menu.lst
cp /boot/grub/menu.lst.win /boot/grub/menu.lst
```
The other script (linux) will be
```
rm /boot/grub/menu.lst
cp /boot/grub/menu.lst.linux /boot/grub/menu.lst
```

Now create two launchers for thos scripts.  However, the launch command is
```
gksu /boot/grub/windows
```
and the scripts must be executable.  Label the launchers "Boot to Windows" and "Boot to Linux."

You can also make some scripts to do the same in Windows if you load the Windows ext2fs driver.

---

