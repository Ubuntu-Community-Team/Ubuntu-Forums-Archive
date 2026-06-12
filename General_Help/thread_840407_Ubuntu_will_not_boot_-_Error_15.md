---
title: "Ubuntu will not boot - Error 15"
date: 2008-06-25
forum: General Help
---

### Post by raj9786 on 2008-06-25
I know this has been brought up many times but I am getting an Error 15 - file not found when I try to boot ubuntu instead of xp. I have done searches for this error many times but I have not found a solution that works for me. I have 1 hard drive but it is partitioned into 3 different drives. on is c which is my windows partition, one is e which i just put my extra junk in, and the last is h, which has my ubuntu installation and some other files. I am a new ubuntu user and I installed ubuntu (8.04) as an "application" in windows. When i start my computer i get the option of choosing windows or ubuntu but when i pick ubuntu, i get the error 15. Am i doing something stupid? Anyone have any suggestions? Thank you for your help.

---

### Post by logos34 on 2008-06-25
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

---

### Post by dracayr on 2008-06-25
press 'c' in the menu. then, type "find /boot/grub/stage1" (without the quotes). It should give an output of the type (hdX,X). write that down. then, press esc. You should come back to the menu. Select the ubuntu entry and press 'e'. select the line with (hdY,Y), press 'e' and change it to the Value you wrote down earlier, (hdX,X). Then press enter and then 'b'

dracayr

---

### Post by raj9786 on 2008-06-25
thanks for your tips. dracayr, i tried what you suggested. When i type find /boot/grub/stage1 i get the same "error 15 file not found" message. logos 34, i clicked on your link but I could not find any information pertaining to my particular problem. thanks for the help guys

---

### Post by logos34 on 2008-06-25
> **raj9786 said:**
> dracayr, i tried what you suggested. When i type find /boot/grub/stage1 i get the same "error 15 file not found" message. logos 34, i clicked on your link but I could not find any information pertaining to my particular problem. 

huh?  Did you let the page load? (takes a full minute--it's huge).  I gave you the exact link.

What about trying this:

> "...remove the corrupted files and replacing them with new ones. 
                                       First, save your menu.lst (or grub.conf), to your /home/username folder to get it in a safe place until you are ready to restore it again.  Then remove all those bad files in /boot/grub. Copy back your menu.lst, and reinstall [COLOR=#000000]GRUB[/COLOR]. Here are the commands,
                                       Code:
                                                                                                                                                                           sudo cp /boot/grub/menu.lst .
                                       sudo rm /boot/grub/*
                                       sudo cp menu.lst /boot/grub
                                       sudo grub-install /dev/hda"Since you can't boot into ubuntu, you'll have to do it from live cd.  Mount root partition, and then adjust the paths accordingly (root should mount at '/media/disk').  Change the last command to 

                                       sudo grub-install **--root-directory=/media/disk** /dev/sda

Corrupt and/or missing grub files certainly is a possibility (after all, you can't find stage1)...Either that or try a filesystem check/repair:

** sudo fsck /dev/sda1**

(or whatever root is.  Make sure root is unmounted before you do this)

Or else dl **Super Grub Disk**

---

