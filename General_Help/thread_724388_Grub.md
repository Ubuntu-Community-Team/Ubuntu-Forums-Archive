---
title: "Grub"
date: 2008-03-14
forum: General Help
---

### Post by aravindas on 2008-03-14
Hello,
I need help setting up dual boot with WinXP and Ubuntu.  I am using the GRUB boot manager, which comes with Ubuntu by default.  Also, I have previously setup dual boot with GRUB.  However, this time I have installed each of them on different hard discs.  At present, to boot to Ubuntu, I need to go to BIOS and change the boot sequence to SCSI, C.. I am changing the boot sequence to C,SCSI to boot to Windows.  It is pain doing this everytime. I know it is possible with GRUB, but out of ideas.  GRUB is installed on Ubuntu disc(I pressume it is SCSI, from BIOS). When I boot to Ubuntu, the windows disc can be accessed from /dev/sda1.  I tried editing /boot/grub/menu.lst with various combinations of root(hd0,0), root(hd0,1), root(hd1,0), root(hd1,1), root(sd0,0), root(sd0,1), root(sd1,0) and root(sd1,1). It didnt boot to Windows XP in either of these cases. Either I get error "Invalid Parameter" or it shows "Starting Up" and does nothing.  I really need help. 

Thank you so much,
Aravinda

---

### Post by kyphi on 2008-03-14
The way to dual boot with two hard drives is to install Windows first on one drive and then install Ubuntu on the other drive.

Ubuntu will write a boot menu (GRUB) with an added section to the Windows boot sector (MBR).

If all else fails just reinstall Ubuntu on your second drive.

If you had a GRUB boot menu and have damaged it you can try the following sequence in a terminal:
```
sudo grub
```
```
find /boot/grub/stage1
```

This will return a value (hdx,y) - take note of x and y and enter these values into the next command.

```
root (hdx,y)
```
```
setup (hd0)
```

0 is the number zero

Then quit, exit and reboot.

---

### Post by sancho panza on 2008-03-14
Try and see if the Super [grub disk utility]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#introduction") helps.

---

