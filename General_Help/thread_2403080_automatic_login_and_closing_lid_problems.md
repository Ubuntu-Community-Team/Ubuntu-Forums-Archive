---
title: "automatic login and closing lid problems"
date: 2018-10-07
forum: General Help
---

### Post by ozaru on 2018-10-07
Hello, I have problems with automatic login. Then I start up computer I have to every time enter pass,but in settings is on. And in settings where is no option  what does when i close lid on laptop. And then I close lid its puts on sleep computer but I don't want this so how to fix this I using ubuntu 18.04 with gnome?

---

### Post by coffeecat on 2018-10-07
Support, not chat.

*Thread moved to **General Help**.*

---

### Post by #&amp;thj^% on 2018-10-07
For the AutoLogin lets have a look at this file:
Run in terminal:
```
gedit /etc/gdm3/custom.conf
```
paste back so we can see.
It is best to ask only one question per thread to avoid confusion. ;)

---

### Post by ozaru on 2018-10-07
# GDM configuration storage
#
# See /usr/share/gdm/gdm.schemas for a list of available options.

[daemon]
AutomaticLoginEnable=True
AutomaticLogin=ozr

# Uncoment the line below to force the login screen to use Xorg
#WaylandEnable=false

# Enabling automatic login

# Enabling timed login
#  TimedLoginEnable = true
#  TimedLogin = user1
#  TimedLoginDelay = 10

[security]

[xdmcp]

[chooser]

[debug]
# Uncomment the line below to turn on debugging
# More verbose logs
# Additionally lets the X server dump core if it crashes
#Enable=true

---

### Post by #&amp;thj^% on 2018-10-07
Try changing your:
```
[daemon]
AutomaticLoginEnable=True
AutomaticLogin=ozr
```
To:
```
[daemon]
AutomaticLoginEnable = true
AutomaticLogin = ozr
```
Notice "True" was changed to "true" and spaces was added.
To make those changes use:
```
sudoedit /etc/gdm3/custom.conf
```
**Important save the file before closing the terminal.  **
Now test to see if is it now working with a reboot.
Then we can see if i can help with your closing lid problem.

---

### Post by ozaru on 2018-10-07
sorry this doesnt helps

---

### Post by #&amp;thj^% on 2018-10-07
Works for me and others???
Next then we will also edit that same file this time changing:  **"sudoedit /etc/gdm3/custom.conf"**
```
# Uncoment the line below to force the login screen to use Xorg
#WaylandEnable=false
```
To:
```
# Uncoment the line below to force the login screen to use Xorg
WaylandEnable=false
```
And again reboot>>>Are you using a Nvidia Card and driver?
Also show this:
```
inxi -SG
```
EDIT: I don't have time to wait hours for a reply today so i will check back later. :P

---

### Post by ozaru on 2018-10-08
thanks now works

---

### Post by ozaru on 2018-10-08
System:    Host: ozr Kernel: 4.15.0-36-generic x86_64 bits: 64
           Desktop: Gnome 3.28.3 Distro: Ubuntu 18.04.1 LTS
Graphics:  Card-1: Intel 3rd Gen Core processor Graphics Controller
           Card-2: NVIDIA GK208M [GeForce GT 740M]
           Display Server: x11 (X.Org 1.19.6 ) drivers: i915,nouveau
           Resolution: 1366x768@60.06hz
           OpenGL: renderer: Mesa DRI Intel Ivybridge Mobile
           version: 4.2 Mesa 18.0.5

---

### Post by #&amp;thj^% on 2018-10-12
> **ozaru said:**
>  And in settings where is no option  what does when i close lid on laptop. And then I close lid its puts on sleep computer but I don't want this so how to fix this I using ubuntu 18.04 with gnome?
This is for Lid-Closing options
For those who want it to automatic shutdown, hibernate, or do nothing when laptop lid is closed, here’s how to do it by editing the configuration file.

1. Open terminal and run this command:
```

sudoedit /etc/systemd/logind.conf
```

When the files opens, uncomment the line "**#HandleLidSwitch=suspend"** by removing "#" in the beginning, and change the value to:
Options are:
```

    HandleLidSwitch=poweroff, shutdown / power off when lid is closed.
    HandleLidSwitch=hibernate, hibernate when lid is closed (**Warning** you will need to test if hibernate works).
    HandleLidSwitch=ignore, do nothing.
    HandleLidSwitch=suspend, suspend laptop when lid is closed.
```

Now Save the file and finally restart the Systemd service to apply changes via:
```

systemctl restart systemd-logind.service
```

---

### Post by Leslea_kate on 2018-10-31
Thanks 1fallen, that solved the issue for me too!  (Dell  E4310 laptop).

Leslea

---

