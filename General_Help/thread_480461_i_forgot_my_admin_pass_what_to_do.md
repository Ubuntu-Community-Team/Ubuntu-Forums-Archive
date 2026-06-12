---
title: "i forgot my admin pass what to do?"
date: 2007-06-21
forum: General Help
---

### Post by yaggi07 on 2007-06-21
i cant access the other programs because i forgot my administrator password... can you help me? ty

---

### Post by diatribe on 2007-06-21
if you are using sudo it should be the same password as your regular login

---

### Post by yaggi07 on 2007-06-21
im using ubuntu

---

### Post by TacticalPenguin on 2007-06-21
It's probably the same as your user login password.

---

### Post by yaggi07 on 2007-06-21
is there other way to recover my password??

because im using ubuntu software right now and i disabled windows xp..

so whenever i start the pc it goes to ubuntu...

how can i run windows???

---

### Post by TacticalPenguin on 2007-06-21
Do you still have your ubuntu LiveCD? If so, boot to it, backup any important data, and reinstall ubuntu.

---

### Post by yaggi07 on 2007-06-21
uhm.. how can i run windows xp? without rebooting ubuntu?

---

### Post by harty83 on 2007-06-21
Did you have windows installed when you installed ubuntu?  If so, ubuntu installer probably created a windows option in your grub menu.  When you first boot up, hit esc to get the grub menu.  Select windows if it is there.  You should then boot into windows.  If it is not listed and you are sure it is still in existence, post back and I'll tell you how to modify your grub menu file.

---

### Post by yaggi07 on 2007-06-21
sir i pressed escape just like u said.. but nothing happened.. im sure windows is still here since i used it about 5days ago..

---

### Post by r0ck80y on 2007-06-21
Boot ur computer on an ubuntu liveCD. Enter the liveCD ubuntu desktop environment. Open gnome terminal. Type "sudo su", this makes u "liveCD root". Then mount the partition where ubuntu is installed (say if the partition is /dev/hda2): ```

mount /dev/hda2 /mnt/ubuntu
```
then enter your installed ubuntu as root by typing:```

chroot /mnt/ubuntu /bin/bash
```
Now just type ```
passwd
``` and change your admin passwd for ubuntu
Then exit, reboot into ur installed ubuntu

---

### Post by yaggi07 on 2007-06-21
sir i just need to log in to windows xp right now but the only program that starts is ubuntu...

and any idea how i could run windows xp?

---

### Post by harty83 on 2007-06-21
> **yaggi07 said:**
> sir i pressed escape just like u said.. but nothing happened.. im sure windows is still here since i used it about 5days ago..

When did you install ubuntu?  If you have not used windows since you installed ubuntu, it is very possible that you wiped out windows.

Make sure you press esc when you see:

[CODE]GRUB Loading stage1.5.

GRUB loading, please wait
Press 'ESC' to ender the menu.../CODE]

---

### Post by Qu4k3R on 2007-06-21
And open a terminal:

Press "Ctrl+Alt+F2" and execute:

> 
gnome-terminal


(or konsole if you are using Kubuntu)

After you have your shell,
do this:

> 
gedit /boot/grub/menu.lst


use kate instead of gedit if you are using kubuntu.

There must be a "section" where grub lists the option of starting Windows instead of Ubuntu.

---

### Post by yaggi07 on 2007-06-21
my brother installed this software.. he can use windows also.. when you start the computer, after booting i see a menu.. select on of working systems i think.. i will choose whether ubuntu blah blah or windows xp..

when i choose windows xp i can use windows xp..

but now i cant see it anymore.. probably he changed a setting somewhere..

---

### Post by r0ck80y on 2007-06-21
Just follow Qu4k3R's last post. Open the 'menu.lst' file and see if in it there are lines which read similar to the ones below: ```

title Windows XP 
rootnoverify (hd0,0)
makeactive
chainloader  +1

```
If not , then add them to the file. Replace '(hd0,0)' with the partition where xp is installed. Save the file and reboot.

---

### Post by harty83 on 2007-06-21
Okay so you do need to edit your grub menu file.  

If you have not figured out your password yet, do what r0ck80y said to do.  Then you need to log in to ubuntu.

Hold down alt then press F2.  Type in "gksu gedit /boot/grub/menu.lst"

Add the following to the very bottom:
```

title		Windows
root		(hd0,0)
makeactive
chainloader	+1

```

Make sure this is after "### END DEBIAN AUTOMAGIC KERNELS LIST."

This is assuming that your windows is installed on the first partition of your first harddrive.  Change (hd0,0) to match your setup.  If your windows is installed on the first partition of a second hard drive then it would be (hd1,0).  If you don't know, try what I have first then post back.]

OH yea, make sure you save! Then reboot and try to boot into windows.

---

