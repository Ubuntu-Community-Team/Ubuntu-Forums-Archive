---
title: "Access grub menu on a hp notebook in ubuntu 14.04"
date: 2016-11-02
forum: General Help
---

### Post by fajeth on 2016-11-02
As the title says. The shift key is not working for some reason. Any suggestion would be appreciated.

---

### Post by ajgreeny on 2016-11-02
Is it a UEFI machine instead of MBR?  

If UEFI it is probably holding or continuous tapping of Esc key, though I have to say, it did not work for me.
I have therefore edited my **/etc/default/grub** file and then run command  ```
sudo update-grub
``` to ensure the menu always shows for 2 seconds in my single-OS machine, just in case I ever have a situation where I need to boot to an earlier kernel. A 2 second delay in booting is not worrying me.
```
GRUB_DEFAULT=0
#Next line will make the countdown time show menu by default
GRUB_TIMEOUT_STYLE=menu
#Next line changed from 0 to 2 for 2 second delay
GRUB_HIDDEN_TIMEOUT=2
#Next line changed from true to false to allow delay countdown to show
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR="Xubuntu-14.04"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```

---

### Post by fajeth on 2016-11-02
Esc did the trick. Odd. I thought it was for older versions. Anyway thank you.

---

### Post by ajgreeny on 2016-11-03
Great! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

