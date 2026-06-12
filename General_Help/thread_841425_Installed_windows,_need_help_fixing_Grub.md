---
title: "Installed windows, need help fixing Grub"
date: 2008-06-26
forum: General Help
---

### Post by spiritfox on 2008-06-26
I have used ubuntu for about a year as the only OS on my hp laptop.  Recently i needed Windows for work.  I ran the gparted live cd and resized my old partition, making room for a 12Gb windows partition, which I then installed windows on.  I forgot, of course, that Windows changes the mbr without asking.  How do I get Grub back so I can load ubuntu again?  I can get a backup of all my data by removing the hard disk and plugging it into an adapter, but i would prefer not to need to reformat anything.  Any help is appreciated.

---

### Post by jualin on 2008-06-26
Check out this program, everyone in the forums seem to suggest it every time someone ask your question.[www.supergrubdisk.org/]("www.supergrubdisk.org/") Hope you like it!

---

### Post by spiritfox on 2008-06-26
disc worked perfectly and i booted back into linux easily!  Now i just need to know how to edit grub to point to windows...

---

### Post by WRDN on 2008-06-26
> **spiritfox said:**
> disc worked perfectly and i booted back into linux easily!  Now i just need to know how to edit grub to point to windows...

Could you please type:

```
fdisk -l
```

. . . in the terminal and paste the output here.

The GRUB file is located in /boot/grub/menu.lst

Please could you post the contents of that file here to.

_______

At the bottom of my menu.lst file (dual booting Ubuntu and XP Home Edition) it says:

```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

You need to add this, and you may need to change the line, "root (hd0,0)".

When I type fdisk -l, I get the following output:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13212   106125358+   7  HPFS/NTFS
/dev/sda3           13213       14946    13928355    5  Extended
/dev/sda5           14868       14946      634536   82  Linux swap / Solaris
/dev/sda6           13213       14791    12683254+  83  Linux
```

As can be seen, Windows is located (for me), on /dev/sda1.
With the numbers in the menu.lst file, you start counting at 0, hence "root (hd0,0)" refers to /dev/sda1.

You need to edit your file and just change the device number, depending upon which device Windows is on.

---

### Post by drs305 on 2008-06-26
> **spiritfox said:**
> disc worked perfectly and i booted back into linux easily!  Now i just need to know how to edit grub to point to windows...

The safest and perhaps easiest way is to edit the grub menu via StartUp-Manager. You can select which OS to boot, menu delays, how many kernels to display, etc. And you don't run this risk of messing it up with an editing mistake.

Install it with:
```
sudo aptitude install startupmanager
```

Access it via: System > Admin > StartUp-Manager

Learn what you can do with it:
[HOWTO: Grub Menu Kernel Display Options & StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

---

