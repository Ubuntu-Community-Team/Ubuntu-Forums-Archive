---
title: "Desktop icons do not stay where put after reboot"
date: 2020-09-01
forum: General Help
---

### Post by Jonners59 on 2020-09-01
I have been having a bit of a frustrating time lately.  I have found after the last version upgrade that none of my PCs and laptops keep the desktop as layout after a reboot.  Searching the forum and Google I have not found anything that works.
 One of the things I have tried is this cmd
```
sudo chattr +i ~/.config/xfce4/desktop/icons*
```
```
sudo chattr -i ~/.config/xfce4/desktop/icons*
```

tried this too
```
sudo ls /home/media/.config/xfce4/desktop/
```
Which gives:
[HTML]icons.screen0-1854x997.rc  icons.screen0-1904x1039.rc
icons.screen0-1868x997.rc  icons.screen0-1904x997.rc[/HTML]
```
sudo rm /home/media/.config/xfce4/desktop/icons.screen0-1854x997.rc
```

FYI
```
sudo uname -a
```
```
Linux Media-Server 5.4.0-45-generic #49-Ubuntu SMP Wed Aug 26 13:38:52 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```

If anyone can help, please????

---

