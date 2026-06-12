---
title: "&quot;Restore point&quot; or software available to reset Ubunu on reboot?"
date: 2006-10-17
forum: General Help
---

### Post by emarkay on 2006-10-17
I have always disabled that feature in WinXP, but some use it, and in an environment where you have PC's that are configured correctly, and you want them to stay that way (a school or library for instance) there are software packages (Deep Freeze is one - [http://www.faronics.com/html/deepfreeze.asp](http://www.faronics.com/html/deepfreeze.asp) ) that remove anything added or changed upon reboot.

Is there anything in Ubuntu for that?

---

### Post by kuja on 2006-10-17
I'm not sure it would be a major issue. So long as a user doesn't have root access, it's **impossible** to do damage to the system settings (only to the user settings).
If you want a fallback, the safest approach is probably to create a backup of the partition with something like partimage. Unless you're messing with things as root that you shouldn't be messing with this should be a non-issue though.

---

### Post by emarkay on 2006-10-17
OK, but more likely what happens if someone adds or deletes programs, changes default screen savers, deletes fonts, plants a malware file, or other things that a "badguy" may be wont to do when at an unsupervised computer?

---

### Post by kuja on 2006-10-17
Adding and deleting programs isn't possible without root access. Deleting fonts without root access isn't possible. Most forms of  malware doesn't exist in linux to the extent of my knowledge, and for one to do crippling damage it would need root access too.

---

### Post by kuja on 2006-10-17
My further advise is to implement a BIOS password, make sure booting by things other than the primary hard drive is disabled, and to set a bootloader(grub) password. Unless said "bad guy" opens the computers case and resets the bios/bios password, this should be secure enough.

Granted, you'll also want to set up a "guest user" account or something of the like. It shan't  be a member of any privileged groups(especially not the admin group).

---

### Post by argie on 2006-10-17
Or you could setup your computer the way you like it, and back it up with partimage. Then restore that when you want.

A list of other programs here:
[http://www.ubuntuforums.org/showthread.php?t=126930](http://www.ubuntuforums.org/showthread.php?t=126930)

---

