---
title: "Computer Disk Error problems. D="
date: 2008-01-16
forum: General Help
---

### Post by tenkabuto on 2008-01-16
I've been Googling and trying different things in the XP Recovery Console from my XP CD, but nothing has allowed me to get to the OS selection menu! It was working fine yesterday, but today I turn on the computer and it goes past the Dell Splash for pressing F2/F12, then doesn't load the menu! Instead it reads:
> Disk error
Press any key to restart.

Pressing any key, I may add, doesn't restart the computer, but only displays a duplicate of the error message!

Oh, also, I have the following:
1GB Flash Drive, don't know if this could help somehow.
Ubuntu Linux Live CD
Windows XP Disc

If you can help me fix this I'll really appreciate it. You guys have helped me many times in the past, thanks so much. =]

---

### Post by rocketman768 on 2008-01-16
Did you have Ubuntu installed and simply overwrite the MBR? If so, your boot up configuration files (namely /boot/grub/menu.lst) still exist on the hard drive and you can just reinstall grub with the Ubuntu Live CD by doing this: [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by tenkabuto on 2008-01-16
I have a problem though, I _can't_ get into the Live CD! When I try I get the same "Disk error" message!

---

### Post by Craigus on 2008-01-16
So, you can boot from the XP CD but not the linux one ?

---

### Post by tenkabuto on 2008-01-16
Strangely yes. I can fully install or even format a partition with the XP disc, but after that XP doesn't work either. =/

---

### Post by tenkabuto on 2008-01-16
Bump? x__x

---

### Post by tenkabuto on 2008-01-16
Please reply! DX

---

### Post by rocketman768 on 2008-01-16
You would not get a disk error message from the BIOS unless it either did not know to check the CD before the hard drive for a boot sector, OR because you didn't burn the CD right.

This might be obvious, but...
1) Did you burn the .iso image from the live CD correctly? You don't create a data cd and just put the iso file on the disk. You have to burn it as an image (sorry if I am insulting your intelligence).

2) Make absolutely sure that your boot order is configured to check the CD drive before the hard drive. You do this by pressing the correct key at the bootup screen (typically f1, f2, f12, or del).

---

