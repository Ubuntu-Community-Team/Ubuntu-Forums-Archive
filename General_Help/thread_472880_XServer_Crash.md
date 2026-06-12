---
title: "XServer Crash"
date: 2007-06-13
forum: General Help
---

### Post by Arkane on 2007-06-13
I am running a dual-boot Dell Inspiron 6000. All has been well using Ubuntu 6.10 and Windows XP. Since I rarely use the XP, it is not really configured hence the system hibernated after 3 hrs. Today when I boot Linux, everything works, except my login screen is probably at 800x600 Res. My Desktop looks like scrambled eggs at the same Res. The system seems to be intact, restarting X using ctrl+alt+backspace doesn't help. Is there a way to check the integrity of X booting in recovery mode??

Thanks in advance
________________

---

### Post by borris.morris on 2007-06-14
sounds like its just a bad xorg.conf. the way to fix this is "sudo dpkg-reconfigure xserver-xorg" and go through and select the right settings. 

P.S. Make a backup with cp /etc/X11/xorg.conf ~/xorg.conf

---

### Post by Crafty Kisses on 2007-06-14
> **Arkane said:**
> I am running a dual-boot Dell Inspiron 6000. All has been well using Ubuntu 6.10 and Windows XP. Since I rarely use the XP, it is not really configured hence the system hibernated after 3 hrs. Today when I boot Linux, everything works, except my login screen is probably at 800x600 Res. My Desktop looks like scrambled eggs at the same Res. The system seems to be intact, restarting X using ctrl+alt+backspace doesn't help. Is there a way to check the integrity of X booting in recovery mode??

Thanks in advance
________________
You should just reconfigure your X server file, try this:
```
sudo dpkg-reconfigure xserver-xorg
```

That should solve your issue. :p

---

