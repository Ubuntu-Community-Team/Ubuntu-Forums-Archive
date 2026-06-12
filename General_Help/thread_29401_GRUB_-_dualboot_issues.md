---
title: "GRUB - dualboot issues"
date: 2005-04-24
forum: General Help
---

### Post by AvvY on 2005-04-24
I am running a dual boot between WinXP Home Ed and Ubuntu Hoarty Hedgehog 5.04.

I have a master (sata) hdd and a slave (ide) hdd. Winxp is installed on the first primary partition on the master (/dev/sda1) and Ubuntu is installed on the first primary partition on the slave (/dev/hdb1).

I have GRUB installed on the MBR of the slave (ide) hdd - how it automatically installed during setup. It detected winxp on the other partition and added it to GRUB.

because GRUB is installed on the MBR of the slave, i can only boot into Ubuntu if i change the boot order in BIOS of the hdd's. When i boot the slave GRUB loads with all the Ubuntu options and winxp listed. if i select winxp i get the following error:

Booting 'Microsoft Windows XP Home Edition'
root (hd0,0)
file system type is ext2fs, partition type 0x83
save default
make active
chainloader +1

Error 13: Invalid or unsupported executable format.

I think what is happening, is that there is a conflict between GRUB thinking /dev/sda1 is ext2 when it is infact NTFS. I have had a look at /boot/grub/menu.lst but can't figure out what is wrong with the Windows entry in the file.

I figure all i'd need to do is edit this so win boots. or, remove GRUB from the slave (ide) drive's MBR and install it on the master (sata) drive's MBR.

Any ideas of what I should go about doing?

Late,

---

### Post by nad on 2005-04-24
The following is a kludge that is making the rounds to load xp. It should work.

Edit your /boot/grub/menu.lst to include only the following lines for your windows installation: (don't forget to modify for your configuration!)

title=anything you wish - this is only a description
map (hd0) (hd1) # Tell the first hard drive to pretend to be the second
map (hd1) (hd0) # Tell the second hard drive to pretend to be the first
root (hd1,0) # Tell GRUB Windows is on /dev/hdb1 (No pretending here)
rootnoverify (hd1,0) # GRUB won't attempt to mount the Windows drive
makeactive # Sets the partition to active
chainloader +1 # Tells GRUB to load the Windows bootloader when done

Please post back with your results.

---

### Post by gizmospc on 2005-04-24
I am having a very similar problem on my system, only difference is that my master and slave drives are both ide.  I know somewhere I'm missing a step too because I never see an option as to where to place grub (as in master or slave, windows or linux drive).  Is this a standard part of installation, or do you have to do an 'expert' or custom install?  I'm still pretty new with this, so be gentle ;)

---

### Post by AvvY on 2005-04-24
Thanx for posting. Ok so because winxp is on a stat drive, should the grub menu lines be as follows:

title=Microsoft Windows XP Home Edition
map (hd0) (sda1) # Tell the first hard drive to pretend to be the second
map (sda1) (hd0) # Tell the second hard drive to pretend to be the first
root (sda1,0) # Tell GRUB Windows is on /dev/hdb1 (No pretending here)
rootnoverify (sda1,0) # GRUB won't attempt to mount the Windows drive
makeactive # Sets the partition to active
chainloader +1 # Tells GRUB to load the Windows bootloader when done

???

I'm really not sure, because from what i have learnt, hd- is for ide drives, and sda- is for sata drives- corrrect?

Thanx again.

Late,

---

### Post by AvvY on 2005-04-24
Also, i found this to reinstall grub. i could just do that and reinstall it on /dev/sda1 right?

grub-install /dev/hda

Although this would conflict with the current grub install on /dev/hda. so as i proposed earlier, i could just uinstall it from the slave MBR and reinstall it to the master MBR using this command? if so, how would i remove it from /dev/hda? - run a win98 floppy with the slave drive as the first hdd to boot and run fdisk /mbr? then reinstall grub? - although then i wouldn't be able to get into ubuntu... any ideas?

Late,

---

### Post by AvvY on 2005-04-26
*bump*

:)

Late,

---

### Post by malacoda on 2005-05-09
Hey Avvy,

I'm having the same issue you are.  In your message thread you listed a few options you were going to try: mapping the drives so GRUB thought the secondary SATA was really the primary drive and uninstalling GRUB from the MBR of your secondary drive and reinstalling it on the primary...

Did you ever get it to work and if so, which of these two approaches (or any other approach) did the trick?

Would appreciate any help or insight you could provide on getting GRUB to work w/ WinXP on a SATA and Ubuntu on an IDE...

thanks,
Malac

---

### Post by c_dog on 2005-05-09
[QUOTE=AvvY]Thanx for posting. Ok so because winxp is on a stat drive, should the grub menu lines be as follows:

title=Microsoft Windows XP Home Edition
map (hd0) (sda1) # Tell the first hard drive to pretend to be the second
map (sda1) (hd0) # Tell the second hard drive to pretend to be the first
root (sda1,0) # Tell GRUB Windows is on /dev/hdb1 (No pretending here)
rootnoverify (sda1,0) # GRUB won't attempt to mount the Windows drive
makeactive # Sets the partition to active
chainloader +1 # Tells GRUB to load the Windows bootloader when done

???

I'm really not sure, because from what i have learnt, hd- is for ide drives, and sda- is for sata drives- corrrect?

Thanx again.

Late,[/QUOTE]

Nope, GRUB reads the BIOS tables and references all hard disk devices (SCSI, IDE, USB, PCMCIA) as 'hd'. It isn't until the device.map loads do they get their Linux device names. The hdx numbers are in the order that BIOS reads them. So, if GRUB (>v 0.95) isn't still pickiing up the change from  a remapping in the menu.lst, you may need to manually edit the device.map and grub.conf files

---

