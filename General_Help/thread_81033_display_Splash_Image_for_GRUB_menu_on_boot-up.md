---
title: "display Splash Image for GRUB menu on boot-up?"
date: 2005-10-23
forum: General Help
---

### Post by heart_reaver on 2005-10-23
The following i have done to get splash screen at Grub menu


Q: How to display Splash Image for GRUB menu on boot-up?

   1. Read General Notes

   2.e.g. Assumed that hd0,1 is the location of Ubuntu boot partition

   3.

wget -c [http://frankandjacq.com/ubuntuguide/ubuntu.xpm.gz](http://frankandjacq.com/ubuntuguide/ubuntu.xpm.gz)
chmod 644 ubuntu.xpm.gz
sudo mkdir /boot/grub/images
sudo cp ubuntu.xpm.gz /boot/grub/images/
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst

   4. Find this section

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.
...

   5. Add the following line below it

splashimage (hd0,1)/boot/grub/images/ubuntu.xpm.gz


as per given at [http://www.ubuntuguide.org/#displaysplashimagegrub](http://www.ubuntuguide.org/#displaysplashimagegrub)

but i am getting black screen. 

If any one have installed splash screen in 5.10 do include there file description and 
ideas in details

:D

---

### Post by heart_reaver on 2005-10-23
I have follow following steps  for display Splash Image for GRUB menu on boot-up


======================================
Q: How to display Splash Image for GRUB menu on boot-up?

   1. Read General Notes
   2. e.g. Assumed that hd0,1 is the location of Ubuntu boot partition

   3.
wget -c [http://frankandjacq.com/ubuntuguide/ubuntu.xpm.gz](http://frankandjacq.com/ubuntuguide/ubuntu.xpm.gz)
chmod 644 ubuntu.xpm.gz
sudo mkdir /boot/grub/images
sudo cp ubuntu.xpm.gz /boot/grub/images/
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst

   4. Find this section

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.
...

   5. Add the following line below it

splashimage (hd0,1)/boot/grub/images/ubuntu.xpm.gz



=============================================

But black screen is coming

---

### Post by Iandefor on 2005-10-23
as far as I know, hd0,1 indicates hard disk 0, second partition (Start counting from 0, thus 0 is first, 1 is second, etc, etc). If your Ubuntu installation is in the first partition (Most likely), change all the instances of hd0,1 to hd0,0

Hope this helps.

---

### Post by heart_reaver on 2005-10-28
Hi Iandefor

well i am showing you my fstab file contents then tell me what should it be 


==========================================================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda8       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /mnt/c  vfat    iocharset=utf8,umask=000   0       0
/dev/hda5       /mnt/d  vfat    iocharset=utf8,umask=000   0       0
/dev/hda6       /mnt/e  vfat    iocharset=utf8,umask=000   0       0

================================================


I have tried

splashimage (hd0,7)/boot/grub/images/grubuntu.xpm.gz

and 

splashimage (hd0,1)/boot/grub/images/grubuntu.xpm.gz
:confused:

---

### Post by xyzzyman on 2005-10-28
Wouldn't it be (hd0,6)??? Look farther down in your menu.lst, and see what drive it's loading your linux kernel from. My fstab says sda5, so I use (hd0,4) in my menu.lst

---

### Post by Efwis on 2005-10-28
[QUOTE=heart_reaver]The following i have done to get splash screen at Grub menu


Q: How to display Splash Image for GRUB menu on boot-up?

   1. Read General Notes

   2.e.g. Assumed that hd0,1 is the location of Ubuntu boot partition

   3.

wget -c [http://frankandjacq.com/ubuntuguide/ubuntu.xpm.gz](http://frankandjacq.com/ubuntuguide/ubuntu.xpm.gz)
chmod 644 ubuntu.xpm.gz
sudo mkdir /boot/grub/images
sudo cp ubuntu.xpm.gz /boot/grub/images/
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst

   4. Find this section

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.
...

   5. Add the following line below it

splashimage (hd0,1)/boot/grub/images/ubuntu.xpm.gz


as per given at [http://www.ubuntuguide.org/#displaysplashimagegrub](http://www.ubuntuguide.org/#displaysplashimagegrub)

but i am getting black screen. 

If any one have installed splash screen in 5.10 do include there file description and 
ideas in details

:D[/QUOTE]
its not working because you have the the splashimage in the wrong place.

[color=red]**NOTE:** make a backup of your menu.lst file before attempting the change. To do this type the following in Terminal
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```[/color]

next type the following so you have permission to change the file.
```
sudo gedit /boot/grub/menu.lst
```

In your menu.lst remove all entries regarding your splash image that you have already put in. then find this section
```

# Pretty colours
#color cyan/blue white/blue
```
right below this section you want to add your image entry as shown below.

```
## Splash image!
splashimage (hd1,0)/boot/grub/images/ubuntu.xpm.gz

```

so you should end up with this.

```
# Pretty colours
#color cyan/blue white/blue
## Splash image!
splashimage (hd1,0)/boot/grub/images/ubuntu.xpm.gz
```
You have to know where your grub loader boots from. the easiest way to locate this is by scrolling down in your menu.lst file and finding this entry.

```

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot
```

you want to use the same value as listed here
```
root		(hd1,0)
```

save the file and reboot. you should now see your grub splash image.

---

### Post by Efwis on 2005-10-29
the answer to the issue stated here is given in this thread in the desktop support area.

[http://www.ubuntuforums.org/showthread.php?t=81005](http://www.ubuntuforums.org/showthread.php?t=81005)

the first thing to point out is that the location for the placement and the coding syntax of the splash image line is incorrect.

second of all, the location of the Grub menu is not found through fstab, but in the grub menu.lst itself.

---

### Post by ubuntu_demon on 2005-11-07
heart_reaver I have merged your two threads. Please don't double post.

---

