---
title: "Converting to Ubuntu only"
date: 2024-05-01
forum: General Help
---

### Post by Alligator on 2024-05-01
I just bought a new laptop and got sick of Windows 11 in a real hurry.  I made a bootable usb with 24.04 Lts and I can't get past the MS key required.  It's like trying to hit a moving target.  Is it possible to defeat this road block or should I give the laptop to my granddaughter?

Ron

---

### Post by oldfred on 2024-05-01
Backup Windows before you delete it.
We find many who totally erase Windows, then later find one app or game they have to have that only runs in Windows.

Make sure UEFI & SSD firmware are up to date. 
A few systems still only make that easy from Windows. 
Linux now has fwupdate that works for many systems. And only those systems should be the ones you consider if purchasing a new system.
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)

If Windows fast startup which sets hibernation or hibernation is on, the Linux NTFS driver cannot see the drive.
Make sure Windows fast startup is off.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/](https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/)

What brand/model system. What video card/chip? 
Some require special settings.

Be sure to boot installer in UEFI boot mode. Some newer systems now are UEFI only.
[https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview)
[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

---

### Post by Alligator on 2024-05-02
I didn't see any hp laptops on the list.

---

### Post by yancek on 2024-05-02
In addition to going through the steps suggested in post 2, what software did you use to write the Ubuntu iso to the usb?  Did you verify the download before writing to the usb?  Best to shrink the largest windows partition from windows Disk Management tool so you have free space on which to install Ubuntu.  After booting the usb, what do you see when you try to boot it, what MS key are you referring to?

---

### Post by yancek on 2024-05-02
In addition to going through the steps suggested in post 2, what software did you use to write the Ubuntu iso to the usb?  Did you verify the download before writing to the usb?  Best to shrink the largest windows partition from windows Disk Management tool so you have free space on which to install Ubuntu.  After booting the usb, what do you see when you try to boot it, what MS key are you referring to?

---

