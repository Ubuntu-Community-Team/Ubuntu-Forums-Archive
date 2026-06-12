---
title: "Problem: Laptop will not boot AT ALL"
date: 2007-07-30
forum: General Help
---

### Post by imsodamnhappy on 2007-07-30
I used wubi to install the dual boot on my laptop and everything went very smoothly until I tried to boot it up. It just shut off the laptop and restarted back to the boot menu. I tried to boot Windows and same thing. I tried to boot all options (safe mode, last known good config, restore) and it just shuts off and restarts back to the boot menu. The only way I can get my laptop to boot is using my fedora core CD. 

I desperately need help with this.

I am running XP Media Center Edition normally.

PS. I am downloading Knoppix right now. I hope this will help. From what I understand I will be able to access the ntfs drives using it and hopefully be able to fix any problem I may have, but any other help would be greatly appreciated.

---

### Post by acowboydave on 2007-07-31
There is a thread about this hear>[http://ubuntuforums.org/archive/index.php/t-461277.html](http://ubuntuforums.org/archive/index.php/t-461277.html) , maybe Super Grub may help you boot into windows?  super grub> [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by ago on 2007-07-31
This can happen after a hard reboot. Running chkdisk, possibly from windows CD, normally fixes the issue.

---

### Post by superbungalow on 2007-08-01
If you want a quick fix, try booting in safe mode, hold down the off button so it turns off while it is loading the files. Then boot it back up and it should ask to do a system restore, which should restore back to your last restore point (probably the last time you installed a program).

---

