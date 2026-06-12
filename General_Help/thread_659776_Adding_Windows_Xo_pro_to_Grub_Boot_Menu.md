---
title: "Adding Windows Xo pro to Grub Boot Menu"
date: 2008-01-06
forum: General Help
---

### Post by LinuxMomiji on 2008-01-06
You see i have one one hard drive 2 partitions one with Ubuntu 7.10 and the other with Windows Xp pro in NTFS. I have read that you can add a menu so i can boot into windows or Ubuntu. Can someone tell me how? I am very new to Linux so i need help ^_^!!

---

### Post by ajmorris on 2008-01-06
Hi there,
to do this, you must edit your /boot/grub/menu.lst file
So go ahead, and open a terminal, (press Alt+F2 and in the box that appears, type gnome-terminal.

Now, this looks a little scary at first, but dont be afraid. In this terminal, type, ```
gksu gedit /boot/grub/menu.lst and press enter
``` (dont worry that when you type in your password, no characters, not even '*' appear, your password is still being entered)

Now, please open another terminal, and in this, type sudo fdisk -l.
Now, this will output all of your partitions, the one you want is the one that has type HPFS/NTFS. This will have a /dev device for it, e.g. /dev/sda1, please use whatever your /dev device is.

Now, back to your /boot/grub/menu.lst file.

scroll down to the very bottom of the file, and add the following entry:
```

title Windows XP
root (hd0,0) This entry here, you must put whatever your output from sudo fdisk -l says, the example here, would have /dev/sda1 as the output, so, this means, that here goes (hd0,#number from sda, eg, sda1 - 1)
savedefault
makeactive
chainloader +1
```

Then once you reboot, you will have an entry in grub, title Windows XP

---

