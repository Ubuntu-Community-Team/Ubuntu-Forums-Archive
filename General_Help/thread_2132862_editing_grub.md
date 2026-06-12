---
title: "editing grub"
date: 2013-04-06
forum: General Help
---

### Post by rweaver4 on 2013-04-06
I have installed Ubuntu 12.10 on a separate disc in a PC running windows 7. I have attempted to edit grub to automatically boot to W7 first but Grub ignores the changes I have tried to make. First I have entered in terminal : sudo gedit /etc/default/grub and changed the grub_default to 4 (which is the hard disk with W7).  I then enter: sudo update-grub. when I access the grub menu, I can see that the default is set to 4, but when I reboot the machine boots to Ubuntu and ignores the changes. Any suggestions ?

---

### Post by JFDsouza on 2013-04-06
Do you have the right number on the menu. The numbering starts with 0. could you post what you have on your menu?
First would be Ubuntu then the recovery if you have updated after that could be the older kernels and then the windows option. 
Did it detect the windows installation ?

---

### Post by grahammechanical on 2013-04-06
There are two commands that I find useful when making changes to Grub. This one you know about ```
sudo update-grub
``` that updates the Grub configuration files and sometimes it is enough. But there is another command that is sometimes needed. ```
sudo grub-install /dev/sdb
```

I am assuming that the Ubuntu hard disk is sdb. If it is sda then change the command to ```
sudo grub-install /dev/sda
``` This command installs Grub into the MBR of the hard disk. I have found that running this second command after running the first command brings the changes into effect.

Regards.

---

### Post by Rebelli0us on 2013-04-06
Just use Grub Customizer.

---

### Post by oldfred on 2013-04-06
This also has a graphic to show the counting of lines, so you know better if you have the correct number. You also can use descriptions.

 [https://help.ubuntu.com/community/Grub2/Submenus](https://help.ubuntu.com/community/Grub2/Submenus)

      
 If grub 1.99 with submenus it is a bit different - drs305
[http://ubuntuforums.org/showthread.php?p=10720316](http://ubuntuforums.org/showthread.php?p=10720316)
find your windows entry in grub.cfg and copy to grub default like this Vista entry - If you edit your windows command use the edited copy as this must match the title exactly:
gedit /boot/grub/grub.cfg
and copy into grub_default  here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new :
With grub 1.99 and submenus
GRUB_DEFAULT="2>Ubuntu, with Linux 2.6.38-7-generic"
#GRUB_DEFAULT=0
# if not a sub-menu item this style works.
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

---

