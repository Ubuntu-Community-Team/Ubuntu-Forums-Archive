---
title: "make default XP in grub"
date: 2007-02-25
forum: General Help
---

### Post by wobniarpro on 2007-02-25
Hi all

finally i have xp/ubuntu with no errors ... now i want to know how can i make make default XP in grub so my pc launch windows after 10 secs in boot menu...


please detailed help ( n00b here )


i found that...


 How to change default Operating System boot-up for GRUB menu

    * Read #General Notes 

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
gksudo gedit /boot/grub/menu.lst

    * Find this line 

...
default     0
...

    * Replace with the following line 

default     X_sequence

    * Save the edited file

---

### Post by wobniarpro on 2007-02-25
X_sequence << what means ?

---

### Post by arkangel on 2007-02-25
set the default  to the XP entry, normally the last one , You have to count from 0

I assume your grub looks  something like this

Ubuntu linux  bla bla
Memory test 
WindowsXP

so edit  menu.lst
# sudo gedit /boot/grub/menu.lst
and change the line  
**default  0**  (some where at the beginning) to 
**default 2**   (or the right order you have )

---

### Post by wobniarpro on 2007-02-25
Done, it was number 4 ^^

I put 3 before but "Other Operating Systems:" also counts as a number

so putting 4 i worked it...

ty
______________


Other thing to see windows stuff in ubuntu every time i will have to put these 2 commands ?

sudo mount /dev/hda1 /windows
gksudo nautilus /windows || gksudo konqueror /windows


thanks in advance

---

### Post by arkangel on 2007-02-26
I am assuming you want to mount your windows partition at  boot time 

this is done by editing the /etc/fstab, this file  mounts the  hard drives at boot times
this is explained  here 
[http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")

open your file 
#sudo gedit  /etc/fstab

and add 
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0 1

first you have to know which device is your windows partition (in my case is hda1), then you need to know which file system you have in windows (WARNING :  By default  is NTFS but there is no  support for writing on your disk, for reading there is no problem though  --proprietary software M$S$ policy--  I have formatted  to fat32 (vfat ) so i can read  and write, to know which file system type 
# sudo gparted  )

---

### Post by streeto on 2007-02-26
Put the desired stanza, i.e., that thing that looks like this (I don't have windows, don't know the exact form)

title		Windows XP etc...
root		(hd0,0)
[...]

before the line

### BEGIN AUTOMAGIC KERNELS LIST

in menu.lst. Then, default 0 will always point to Windows. Setting to some number may break things when you upgrade your kernel packages and the automagic list changes.

Please someone correct me if I am wrong.

---

