---
title: "Hardy Herron install"
date: 2008-05-08
forum: General Help
---

### Post by shalemjale on 2008-05-08
Being a relatively new convert to Linux/Ubuntu, I have never made an upgrade. My current config is 7.10 and I have tweaked it and got it just about where I like it. My concerns about the upgrade are:
* will it mess up my settings causing me to spend numerous hours fixing them?
* does it completely erase files...(need to backup files)..giving a totally new system?
>I am sure I will come up with other questions but the above are my current concerns.
:-k

---

### Post by bmac on 2008-05-08
After watching the posts and noting the number of issues individuals had with the upgrade I would suggest backing up your important data prior to upgrading. **This however, should be performed prior to any software update (my opinion).** Many individuals including myself had few to no problems with the upgrade. But this may not be indicative of all experiences.
If your satisfied with Gusty and as a relatively new Ubuntu user, don't wish to risk modifications or lost data than I would suggest staying with Gusty. At least until the next revision of Hardy is released.
All depends on your personal comfort zone.....

---

### Post by luisromangz on 2008-05-08
My laptop (and my parent's) uprade from Kubunt 7.10 to Kubuntu 8.04 was flawless and fast. It keept all personal settings and asked about what to do with system wide configuration files (such as smb.conf). Things may be different on your hardware, and doing a backup copy of your data is always encouraged when performing an upgrade.

---

### Post by AlanB66 on 2008-05-08
Simple Backup Procedure ...

1. Burn a new CD from Ubuntu (8.04)
2. Insert the CD in your system but DON'T close the drawer
3. Shutdown your system
4. Close the CD/DVD drawer
5. Connect an external USB drive
6. Boot your system from the new CD
7. System -> Administration -> Software Sources -> Check "Community Maintained ... (universe)"
8. OK to "reload" when prompted
9. When "reload" completes, open a terminal
10. Type:
[INDENT]    sudo apt-get update && sudo apt-get install partimage[/INDENT]
11. When done, type:
[INDENT]    sudo partimage[/INDENT]
12. Use the GUI to SAVE your SDA1 partition to a date-stamped folder on your USB drive (found in the /media folder)

If things go awry later, you can always follow the above steps to RESTORE the sda1 partition back to when it all worked just fine.

---

