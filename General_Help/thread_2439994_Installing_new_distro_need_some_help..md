---
title: "Installing new distro need some help."
date: 2020-04-04
forum: General Help
---

### Post by xcfstarflight1 on 2020-04-04
Hi guys!
I want to try out a new distro or flavour are they called? 
Mosly I use linux system that has media converters, I guess all apps are cross distro..
But what I need out of the system is just usability thou I tend mostly to use terminal, but a really nice
looking desktop and environment is good.. Guess all distros has pro's and con's... Would really appreciate
if people can help me on the way :) Just need all my documents and stuff from my home folders so I Can
import them back into the new system. . . 
I would like to try out for example xubuntu or if anyone can recommend some other good distro for me?
What I need to know is how to make a good backup of my data. Like. I could make a .tar archive of the
home folders, but not sure yet as to how I will proceed. 
Xubuntu should run as a login option, but it doesn't so I would like to try installing some other distro.

What are you guys using, what can you recommend and how to back up the data I need? 

Best regards,
Sigurd

---

### Post by TheFu on 2020-04-04
Not all applications are cross-distro.  Some distros have different names for different packages and the package files aren't setup to be installed on Ubuntu-based systems.  However, if you have an 18.04 system and want to try a different 18.04-based DE, that would be fine. In short, there is a limit as to how far off packages can be and work and not screw up the package manager dependencies.

If you like xubuntu, try ubuntu-mate.  But really, you don't need to do a whole new install just to try a different GUI. The OS is not the GUI.  

There are hundreds of thread here about backups.  tar is NOT a good backup tool, unless you have a trivial amount of data, say, less than 500MB.  Anything larger and you really need a good backup tool.  tar was created when 20MB was considered HUGE. Consider that.

When you try different DEs, be certain to use different logins for each test.  Some of the config files are incompatible, so it is possible to end up with a specific user login that doesn't work anymore.

Nobody knows what data you need or where it might be on your system.  Typically, most user data is stored in the user's HOME, but that isn't 100%.   [https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006) has an example, little, script to make a backup.

---

### Post by xcfstarflight1 on 2020-04-04
How do I install the ubuntu-mate GUI on top of my Ubuntu system? I tried several ways to get KODI and Cinnamon to work but I cannot log in with those GUI's.
Please help. Any way to access the GUI and since ubuntu-mate is new to me can you help me with getting it up?

---

### Post by TheFu on 2020-04-04
sudo apt install ubuntu-mate-desktop

You can use **sudo apt search "term"** to find package names.  Or use **synaptic** and scroll those those with "-desktop"
There must be 50 different GUIs.  Think there is an extensive thread here about different ubuntu flavors written by one of the moderators.  Also, if you haven't read this already -   [https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html)   please do.  Really should be one of the first things anybody new to Linux desktops reads.

---

