---
title: "Logon screen no longer loads"
date: 2022-12-19
forum: General Help
---

### Post by italiano1234 on 2022-12-19
My ubuntu was going through an update process when the laptop shutdown due to unplugged power source.  Now instead of the logon screen I get a blank screen with a functional mouse pointer.  Any ideas how it can be fixed?  I have the dual boot setup with Grub menu.

---

### Post by MAFoElffen on 2022-12-20
If you press <Cntrl><Alt><F4> at that point, you may get to vtty4, where you can log in and repair the interrupted upgrade.  

From there, then
```

sudo apt install --fix-broken
sudo dpkg --configure -a
sudo apt update
sudo apt dist-upgrade
sudo apt autoremove
sudo reboot

```

---

