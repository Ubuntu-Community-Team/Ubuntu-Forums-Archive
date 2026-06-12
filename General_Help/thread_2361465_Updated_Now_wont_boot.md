---
title: "Updated Now wont boot"
date: 2017-05-16
forum: General Help
---

### Post by xblinky on 2017-05-16
Ubuntu Updated i rebooted my pc now its stuck in a login loop i tryed XAuthority reinstalling lightdm redoing drivers etc

---

### Post by Xian on 2017-05-17
Here's a couple of things you can try:

Ctrl+Alt+F1 to get to a prompt -> Enter commands below -> Ctrl+Alt+F7 or $ sudo reboot

1. Re-install ubuntu-desktop & ubuntu-session
```
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install --reinstall ubuntu-session
```

If still not working:

2. Create a new user and complete the details ... password, etc.

```
sudo adduser newusername
sudo usermod -a -G sudo newusername
```

Go into /home/oldusername and try renaming your .profile and .Xauthority 
They may be the culprit.

If you get permission issues then as su:

```
chown newusername:oldusername /home/oldusername
```

Lastly check in your /home/oldusername folder to make sure no files are owned by root

---

