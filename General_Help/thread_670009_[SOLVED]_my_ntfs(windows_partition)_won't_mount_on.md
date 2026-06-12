---
title: "[SOLVED] my ntfs(windows partition) won't mount on sda1!!!"
date: 2008-01-17
forum: General Help
---

### Post by jskandhari on 2008-01-17
I had to restore my windows vista due to its frequent bluescreens
THen my grub wasn't working which anyhow i used the live cd and made it to work but
Now my windows partition won't mount on /media/sda1
and when i go to /media/sda1 folder opens but blank
when i go to computer i have the windows partition present but unmounted and when i ask it to mount, it ask for my administer password and after mounting it shows owner as root and mounts it in /media/khalsa (khalsa is the drive name) but prior to restoring vista it use to mount it to sda1 and i want it that way coz all my downloads and everything in here is syncronisd with windows folders even torrents and i have placed all the same stuff back in those folders after restore (had a backup in my external of the stuff)



please help

---

### Post by logos34 on 2008-01-17
the uuid has changed.

Edit fstab:
[B]
gksudo gedit /etc/fstab[/B]

replace 'UUID=' with '**/dev/sda1**' 

or get the new uuid with

**blkid**
[B]
sudo vol_id -u /dev/sda1[/B]

---

### Post by dcstar on 2008-01-17
> **jskandhari said:**
> I had to restore my windows vista due to its frequent bluescreens
THen my grub wasn't working which anyhow i used the live cd and made it to work but
Now my windows partition won't mount on /media/sda1
and when i go to /media/sda1 folder opens but blank
when i go to computer i have the windows partition present but unmounted and when i ask it to mount, it ask for my administer password and after mounting it shows owner as root and mounts it in /media/khalsa (khalsa is the drive name) but prior to restoring vista it use to mount it to sda1 and i want it that way coz all my downloads and everything in here is syncronisd with windows folders even torrents and i have placed all the same stuff back in those folders after restore (had a backup in my external of the stuff)

please help

Boot into Windows and remove the drive label.

---

### Post by dcstar on 2008-01-17
> **logos34 said:**
> the uuid has changed.

Edit fstab--replace 'UUID=' with '/dev/sda1' 

or get the new uuid with

blkid

sudo vol_id -u /dev/sda1

Ubuntu will mount using the partition label (if it is available), if there is no label then it will use the default /dev/xxxn mount name.

---

### Post by jskandhari on 2008-01-17
i have replaced the uuid
here is a copy of my fstab


[COLOR="Red"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=dc82b755-ed22-49a9-ba84-ea107fdf33bd /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=7C04F8B904F8778A /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=2C88743C8874071C /media/sda4     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=74422d2f-a79c-4af4-8abc-96f22bc1a47d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0 [/COLOR]

and then when i goto user terminal and type mount media/sda1 it says
[B]jaszy@jaszy-laptop:~$ mount /media/sda1
mount: only root can mount /dev/sda1 on /media/sda1
jaszy@jaszy-laptop:~$ 
[/B]
earlier it use to say no drive or something so i know it is now reading the partition on sda1 but the point is it is still requesting root user to manually mount it and due to which i am not able to use any of the earlier features not even the wallpaper applet is able to read it neither my torrents nothing please help 


thanks in advance

---

### Post by jskandhari on 2008-01-17
[COLOR="Lime"]**REboot**[/COLOR]
it done only thing required was a reboot after assigning the new uuid
**Thank you all so much for the help:)**

finally i can get back to studies i have my end semester exam tomo

muuhhhhhhhhhaaa

---

