---
title: "Wine problem, won't detect drives"
date: 2007-03-05
forum: General Help
---

### Post by lemmy999 on 2007-03-05
Trying to install wine. It appears to have installed but when i try to configure i get the following output

> chris@chris-desktop:~$ winecfg
err:winecfg:apply_drive_changes   unable to define devicename of 'D:', targetpath of '/home'
err:winecfg:apply_drive_changes   unable to define devicename of 'E:', targetpath of '/media/hda1'
err:winecfg:apply_drive_changes   unable to define devicename of 'F:', targetpath of '/media/hda5'
err:winecfg:apply_drive_changes   unable to define devicename of 'G:', targetpath of '/media/hda6'
err:winecfg:apply_drive_changes   unable to define devicename of 'H:', targetpath of '/media/cdrom0'
err:winecfg:apply_drive_changes   unable to define devicename of 'I:', targetpath of '/media/cdrom1'
err:winecfg:apply_drive_changes   unable to define devicename of 'J:', targetpath of '/home/chris'
chris@chris-desktop:~$ wineserver: could not save registry branch to /home/chris/.wine/system.reg : Permission denied
wineserver: could not save registry branch to /home/chris/.wine/userdef.reg : Permission denied
wineserver: could not save registry branch to /home/chris/.wine/user.reg : Permission denied
chris@chris-desktop:~$ 


Any idea what i am doing wrong??

---

