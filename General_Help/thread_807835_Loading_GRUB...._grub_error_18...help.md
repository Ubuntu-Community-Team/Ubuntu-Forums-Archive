---
title: "Loading GRUB.... grub error 18...help"
date: 2008-05-26
forum: General Help
---

### Post by ricky_bains on 2008-05-26
friends i have 
->SUSE proffesional 9 and WIN XP (dual boot)i
->ntel pentium-4 machine
->128MB of RAM which was working fine. 

After hearing about xbuntu (that it can run in low end machine) i downloaded and installed it on my system. All was fine except the slow speed. 
*The main problem occurred when i turned off my pc and booted again.
whenever i try to boot into it it says
Loading GRUB stage 5....

Loading GRUB..
error 18

My harddisk is 40GB
 with two primary partition of each of 10GB of NTFS format
rest is for linux in extended

if i boot thro Xbuntu CD(Try xbuntu without any change to your system option)it works when i intrupted this option while it loads itself in swap and i restart my system inbetween
 pls help me out

---

### Post by Living2007 on 2008-05-26
You need to re-install Xubuntu because GRUB has failed, backup your data before you proceed

---

### Post by meierfra. on 2008-05-27
All about Error 18:
[URL="http://users.bigpond.net.au/hermanzone/p15.htm#18"]
http://users.bigpond.net.au/hermanzone/p15.htm#18[/URL]


Did you overwrite Suse?  If not click on  FixGrub in my signature for instruction  how to reinstall Grub to get back into Suse.

Grub Error 18 often means that you need to  create a separate boot partition. For more qualified advice boot from the   a Live CD and post the output of 

```
sudo fdisk -l
```

If you know how to mount the Xubuntu partition from the Life CD,  post the content of the file /boot/grub/menu.lst  which can be found on the  Xubuntu partition. (If not, I'll tell you how to do it once I see the "fdisk" data)

---

### Post by LaRoza on 2008-05-27
> **Living2007 said:**
> You need to re-install Xubuntu because GRUB has failed, backup your data before you proceed

Why not just reinstall Grub?

---

### Post by cdtech on 2008-05-27
> *The main problem occurred when i turned off my pc and booted again.
whenever i try to boot into it it says
Loading GRUB stage 5....

There is no stage 5 with the GRUB bootloader. Maybe an error 5.

With the live Ubuntu cd.

When you get to the desktop open a terminal and enter.

sudo grub

This will put you into a "grub>" shell (i.e. the grub prompt). At grub>. enter these commands

grub >find /boot/grub/stage1

Whatever was returned for the find command use it in the next step (you are still at grub>.

grub >root (hd?,?)

Again use the value from the find command i.e. if find returned (hd1,5) then you would enter root (hd1,5)

Next enter the command to install grub to the mbr

grub >setup (hd0)

Then exit the grub shell

grub> quit

Then reboot without the CD.

---

### Post by meierfra. on 2008-05-27
Deleted.

---

### Post by meierfra. on 2008-05-27
> There is no stage 5 with the GRUB bootloader.

More likely stage 1.5

---

### Post by Living2007 on 2008-05-27
> **LaRoza said:**
> Why not just reinstall Grub?
You can reinstall GRUB! How?

---

### Post by LaRoza on 2008-05-29
> **Living2007 said:**
> You can reinstall GRUB! How?

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

