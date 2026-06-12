---
title: "Ubuntu 20.04 login loop"
date: 2020-05-06
forum: General Help
---

### Post by chriswelsh23 on 2020-05-06
I am stuck in a login loop. I can hit CTRL+ALT+F2 and login CLI no problem.

Ran an update and tried this too;
```
sudo vim /etc/default/grub
```

changed;
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to;
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
```

```
sudo update-grub
```
```
sudo reboot
```

Same issue, any ideas?

---

### Post by guiverc on 2020-05-06
A gui login requires space in $HOME (your /home/$USER/ directory; /home/guiverc/ for me) so I'd check you have available disk space in your home directory.

This isn't the only issue, but it's most common in my experience unless it's a new system, changed system (ie. you added additional hardware or details you neglected to tell us).

Use `df -hl`  (disk free, -human output & -local only mostly as I prefer them)

---

### Post by guiverc on 2020-05-06
Also asked on [https://askubuntu.com/questions/1236033/ubuntu-20-04-login-loop](https://askubuntu.com/questions/1236033/ubuntu-20-04-login-loop)

---

### Post by chriswelsh23 on 2020-05-06
Brand new system so that's not it - removed from other forum

---

### Post by guiverc on 2020-05-06
You haven't said if it's a desktop or server, if it's a desktop did you allocate the 25gb minimum space suggested in [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements) (and note space must be available to your $HOME directory, having space available in other locations doesn't GUI workfiles to be created and GUI login to proceed).

---

### Post by chriswelsh23 on 2020-05-06
It's the desktop version on a 256GB hard drive with the defaults installed - no fancy setup as I just needed a working desktop

---

### Post by rbmorse on 2020-05-06
Using an Nvidia GPU with the proprietary Nvidia driver _and_ enabling autologin for your user will cause this behavior. 

If that applies here, you can correct the problem by doing the following: 

Reboot.  When you get to the password dialog at login, don't.  Instead, open a command console (<ctrl><alt><F3>) and log in with your normal credentials there.  You'll see some administrivia and then a command prompt (blinking cursor). 

At the prompt run the command:

sudo dpkg-reconfigure gdm3

when offered the opportunity to select a default display manager, select "lightdm", then <tab> to "ok" and <enter>.   Configure lightdm if prompted. 

Then reboot with the changes enabled: 

sudo reboot -n


When it comes back up go ahead and confirm your username and enter your password into the dialogs.  Your system should boot into the GUI.

  Navigate to settings > users > your user and disable the automatic login option. 

You can continue to run Ubuntu under lightdm (works well for me) or repeat the procedure above to change the default display manager back to gdm3.  

As an alternative, you can also correct this issue by reinstalling the O/S and _not_ selecting automatic logins when the installer sets up the user  account.

Also, you might be able to use the command sudo systemctl stop gdm3 from the command console to kill the display manager rather than having to do the initial reboot.  I just tried it and it works both ways.

---

