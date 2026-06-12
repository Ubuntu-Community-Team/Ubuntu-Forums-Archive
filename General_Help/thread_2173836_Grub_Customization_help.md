---
title: "Grub Customization help"
date: 2013-09-11
forum: General Help
---

### Post by warburp on 2013-09-11
I am trying to make the grub display at my native monitor resolution by going into /etc/default/grub
and changing GRUB_GFXMODE="1920X1080" then performing sudo update-grube but it still displays at a painful resolution of 800x600

---

### Post by grahammechanical on 2013-09-11
Update-grub just updates the Grub configuration files. I often find that I need to do a bit more to get changes to take affect. If you only have one hard disk, then run this

```
sudo grub-install /dev/sda
```

That installs Grub into the MBR of sda. It might make the difference.

Regards.

---

### Post by warburp on 2013-09-11
I have multiple Harddisks with multiple partitions but i can figure out where it goes and i will give it a try

---

### Post by warburp on 2013-09-11
unfortunatly it did not work i no longer even have a grub which is a bit of a perdiciment

---

### Post by Bashing-om on 2013-09-11
warburp; Hi !

Editing the correct grub as per your post works in my case. So now you have lost your booting grub, huh ?

Try this. In bios what is set for the 1st boot priority ? Is that hard drive with 'buntu installed on it ? If so, then can you boot to any 'buntu install by changing the boot priority ? no ->
Then fire up a liveDVD and grub may then be installed to the required hard drive ( so bios can find it !) - as per  grahammechanical's advisement.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by warburp on 2013-09-11
Ubuntu is on the first boot drive and still boots i just dont get my big ol' list of options anymore im trying purging grub and reinstalling it right now attmepting to avoid a liveCD because my CD drive doesnt function

---

### Post by warburp on 2013-09-11
Ubuntu is still bootable which means its still there i just dont get my big ol' list anymore i attempted a purge of ubuntu and reinstall but i get the same result

---

### Post by deadflowr on 2013-09-11
After you ran grub-install, did you run update-grub?
also you could post the output of
```
df -h
```
and either 
```
sudo fdisk -l
```
or
```
sudo parted -l
```
These should give a clearer picture of your current setup.

---

### Post by warburp on 2013-09-11
well the menu is back turns out somehow i ended up installing a legacy grub but the entire thing is reverted to the lovely magenta 800x600 screen even though my /etc/default/grub looks like this

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT="0"
GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="100000"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE="1920x1080"


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


export GRUB_MENU_PICTURE="/home/warburp/Pictures/Firefox_wallpaper.BMP"




below is fidsk -l report


 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     4196351     2097152    b  W95 FAT32
/dev/sda2         4198398    27633663    11717633    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda3        27633664   976770382   474568359+  83  Linux
/dev/sda5         4198400    27633663    11717632   82  Linux swap / Solaris


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xf534b7a3


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *    52436160  1953520064   950541952+   7  HPFS/NTFS/exFAT

---

### Post by warburp on 2013-09-11
I've gotten it working apparently the highest resolution support by my graphics card in grub is 1240x800x32 so after i go the menu back and changed the line to that everything appears to be good thank you for helping me out

---

