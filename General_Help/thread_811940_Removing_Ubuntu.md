---
title: "Removing Ubuntu"
date: 2008-05-29
forum: General Help
---

### Post by cancer10 on 2008-05-29
Hi

I have successfully installed ubuntu with windows XP Pro.

How do I uninstall ubuntu from my comp and recover my precious space in FAT32 format?


Thanx

---

### Post by WRDN on 2008-05-29
I've just removed it today, and installed it again for various reasons.
To remove Ubuntu:

- Boot off the Live CD
- Open the Partition Editor (System > Administration)
- Delete the partitions for Ubuntu 
- Resize the Windows partition to fill the space left
- When you restart the PC, GRUB will no longer boot Windows, so you have to boot the Windows installation disk, press "r" to open the recovery console and enter "fixmbr" to let Windows create a new master boot record and boot properly.

---

### Post by cancer10 on 2008-05-29
Hi

The partition editor does not show anything under it. Any alternate way?

Also, do U have how to make Windows the default OS in boot time? Currently mine id Ubuntu but I wanna change it to windows as default



Thanx

---

### Post by WRDN on 2008-05-29
> **cancer10 said:**
> Hi

The partition editor does not show anything under it. Any alternate way?

Also, do U have how to make Windows the default OS in boot time? Currently mine id Ubuntu but I wanna change it to windows as default



Thanx

For the first question, If the Partition Editor on the Live CD doesnt show the partitions, then you could try using [GParted]("http://gparted.sourceforge.net/") (bootable)

If you want to remove Ubuntu and use Windows only, youll have to use the XP disk and the "fixmbr" command to boot Windows.
There are alternatives, but ive found that the easiest way.
Also, if you keep Ubuntu, you can make Windows boot by default by editing the grub boot loader, found at: /boot/grub/menu.lst"

---

### Post by cancer10 on 2008-05-29
Weird but I do not see a menu.lst under /boot/

infact I do not ahve a grub folder under /boot/


see the screenshot plz

[http://img141.imageshack.us/img141/6237/screenshotcr5.png](http://img141.imageshack.us/img141/6237/screenshotcr5.png)

---

### Post by WRDN on 2008-05-29
> **cancer10 said:**
> Weird but I do not see a menu.lst under /boot/

infact I do not ahve a grub folder under /boot/


see the screenshot plz

[http://img141.imageshack.us/img141/6237/screenshotcr5.png](http://img141.imageshack.us/img141/6237/screenshotcr5.png)

That's very odd.
Check the file structure with nautilus as well.

If the GRUB boot loader appears when you turn the PC on, there must be a menu.lst file. If you are having difficulties finding it, you could always Search for the file (Places > Search for Files).

If the grub folder isnt in the /boot folder, check in the /etc folder instead.

---

### Post by overdrank on 2008-05-29
> **cancer10 said:**
> Weird but I do not see a menu.lst under /boot/

infact I do not ahve a grub folder under /boot/


see the screenshot plz

[http://img141.imageshack.us/img141/6237/screenshotcr5.png](http://img141.imageshack.us/img141/6237/screenshotcr5.png)

Hi and you can use the command 
```
gksudo gedit /boot/grub/menu.lst
```
Using the alt, F2 keys

---

### Post by cancer10 on 2008-05-29
For some reasons my ubuntu would not load. Hence I cannot get in. So is there a way i can do this via command prompt at the time of boot?

If yes how?

---

### Post by WRDN on 2008-05-29
> **cancer10 said:**
> For some reasons my ubuntu would not load. Hence I cannot get in. So is there a way i can do this via command prompt at the time of boot?

If yes how?

You only need to edit the boot loader if you plan to keep Ubuntu and fix any issues you are having. If you want to remove it, just delete the partition and use "fixmbr" on the XP disk.

---

### Post by cancer10 on 2008-05-29
Hi

I plan to keep ubuntu and I wanna edit the boot loader at the time of boot. How?

---

### Post by WRDN on 2008-05-29
> **cancer10 said:**
> Hi

I plan to keep ubuntu and I wanna edit the boot loader at the time of boot. How?

If you can't boot Ubuntu normally, then this is the easiest solution I can think of:

- Boot onto the Live CD, find the menu.lst file and make a copy. Edit the file and put it somewhere on the HDD (if possible).
- Restart the PC, and select "Recovery Mode" at the GRUB menu. Then select the option allowing you to login as root, and replace the original menu.lst file using the one you just edited using the Live CD.

---

### Post by cancer10 on 2008-05-30
I had a hard time removing the partition and get rid of the Ubuntu MBR :(

---

### Post by meierfra. on 2008-05-30
> How do I uninstall ubuntu from my comp and recover my precious space in FAT32 format?

> I plan to keep ubuntu and I wanna edit the boot loader at the time of boot

> I had a hard time removing the partition and get rid of the Ubuntu MBR

I'm utterly confused. What are you trying to do and what have you already done?

---

### Post by cancer10 on 2008-05-30
> **meierfra. said:**
> I'm utterly confused. What are you trying to do and what have you already done?


Initially I was trying to remove ubuntu from my system but since the partition manager didnt show any partitions so i thought lets keep ubuntu but make windows the default boot but i failed to do it. 

So I finally decided to remove ubuntu completely and had to work very hard to remove it from my system.

---

### Post by meierfra. on 2008-05-30
> So I finally decided to remove ubuntu completely and had to work very hard to remove it from my system.

So all your problems are solved?

---

### Post by cancer10 on 2008-05-30
Yes

Thanx

---

