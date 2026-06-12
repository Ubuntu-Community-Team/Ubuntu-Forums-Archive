---
title: "Can't log in?"
date: 2007-02-25
forum: General Help
---

### Post by chickensofdoom on 2007-02-25
[note: dual boot, Edgy/XP] 
So for quite a while, my mouse and keyboard wouldn't work with ubuntu.  I finally got them to work today using the usb-handoff workaround, and successfully logged into Ubuntu.  After starting the system updates, I quickly realized that I had very unsmartly partitioned my hard drive (made my ubuntu partition exactly 2gb). Being new to linux, I figured it'd be easier to change the partitions from windows. I restarted the computer, booted XP, and tried to use Acronis to resize the Ext2 partition with Ubuntu on it.  It didn't work, but also didn't get to the point where it attempted to modify the system in any way.  I decided to see what I could do about it in Ubuntu, so I rebooted and chose Ubuntu from the GRUB.  Now when I get to the login screen, I can type in my name and password, and when I hit enter, the screen goes black and after about 2 seconds it just pops back to the name screen.

Any idea why this would happen?

---

### Post by dcstar on 2007-02-25
> **chickensofdoom said:**
> [note: dual boot, Edgy/XP] 
So for quite a while, my mouse and keyboard wouldn't work with ubuntu.  I finally got them to work today using the usb-handoff workaround, and successfully logged into Ubuntu.  After starting the system updates, I quickly realized that I had very unsmartly partitioned my hard drive (made my ubuntu partition exactly 2gb). Being new to linux, I figured it'd be easier to change the partitions from windows. I restarted the computer, booted XP, and tried to use Acronis to resize the Ext2 partition with Ubuntu on it.  It didn't work, but also didn't get to the point where it attempted to modify the system in any way.  I decided to see what I could do about it in Ubuntu, so I rebooted and chose Ubuntu from the GRUB.  Now when I get to the login screen, I can type in my name and password, and when I hit enter, the screen goes black and after about 2 seconds it just pops back to the name screen.

Any idea why this would happen?

Possibly your have changed the UUID of your Linux partition and now your /etc/fstab file is wrong - and this is preventing a normal login.

At the login screen, press CTRL-ALT-F1 and log in on the text screen, if you can then:
```
sudo ls -l /dev/dsk/by-uuid
``` to see what the codes are, and then:
```
sudo nano /etc/fstab
```
and make sure that this file has the correct UUIDs that your system sees.

When you have finished editing:
```
sudo init 6
``` will reboot the PC (which will hopefully now work).

---

