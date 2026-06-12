---
title: "Cannot eject volume"
date: 2008-04-23
forum: General Help
---

### Post by LausArndon on 2008-04-23
I have wine 0.9.54 installed right now and working great. But when I'm trying to install a multi-disk program, and it prompts me to put in the next cd, I can't because because the CD is "in use" by the installer.

Is there someway to have th cd ejected and the next mounted without having to close the installer?

---

### Post by warp99 on 2008-04-23
Open a terminal and issue the command 'eject' or 'sudo eject' if the former does not work. Place the new CD in the tray then enter 'eject -t' to close the tray. Once the new CD is mounted press continue on the installer. You can tell when the CD is mounted because an icon will appear on the desktop and/or a dialog box will open asking to run the CD contents with an associated program.

---

### Post by LausArndon on 2008-04-23
I've tried that already. This is what happens.

```
keith@Laus:~$ eject
umount: /media/cdrom0: device is busy
umount: /media/cdrom0: device is busy
eject: unmount of `/media/cdrom0' failed
```

---

### Post by mc4man on 2008-04-23
you could try running install from drive_c, cd to it - ex. - ```
doug@doug-desktop:~$ cd /home/doug/.wine/drive_c
doug@doug-desktop:~/.wine/drive_c$ 
```
then ```
wine "D:\setup.exe"
```    (D= drive letter in wine that assigned to cd drive with disk in it. Ck. if different)
 then try various means to eject

---

### Post by LausArndon on 2008-04-23
That worked perfect. Thanks much.

---

