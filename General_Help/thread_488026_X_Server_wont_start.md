---
title: "X Server wont start"
date: 2007-06-29
forum: General Help
---

### Post by mikaelsnavy on 2007-06-29
Hello,
I just attempted to change my Ubuntu feisty login screen and once I rebooted, the "failed to start the X Server" screen came up. I re-installed my drivers (nvidia), replaced xorg.conf with a backup (that I know works), and i did "sudo dpkg-recover xserver-xorg". None of them worked. I also have updates that I installed. I also added avant window navigator to start up automatically in the sessions tool in the preferences menu.

Any ideas??
Thanks,
Mikael

---

### Post by eggdeng on 2007-06-30
On the off-chance that the problem is caused by the entry you added to the Session Startup Programs tab, you can remove it as follows. 
```
ls /home/your_username/.config/autostart
```
You will see a .desktop file for each item on your Startup list. Removing the file removes the item.
```
rm /home/your_username/.config/autostart/whatever.desktop
```
If you haven't tried already, you can revert to the bundled driver by backing up /etc/X11/xorg.conf and changing the line Driver 'nvidia' back to Driver 'nv' in the original file.
Are you able to log on in recovery mode?

---

### Post by mikaelsnavy on 2007-07-01
I fixed it by reinstalling gdm. Thanks!

---

