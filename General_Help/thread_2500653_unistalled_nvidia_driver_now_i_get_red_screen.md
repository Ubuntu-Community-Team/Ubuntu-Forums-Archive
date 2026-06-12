---
title: "unistalled nvidia driver now i get red screen"
date: 2024-09-08
forum: General Help
---

### Post by yurifss99 on 2024-09-08
so im a noob on ubuntu, i was trying to change my nvidia drivers from 560 to 545 and i used some commands to uninstall, for sure i made some mistake and used a command that i shouldn't now when i boot my pc i get a red screen on the user page and aafter i type my password the screen goes all black: [https://imgur.com/a/bG5SXPp](https://imgur.com/a/bG5SXPp). If i boot my pc on recovery mode it works like nothing happened: [https://imgur.com/a/bjcLFJk](https://imgur.com/a/bjcLFJk), can someone help me solve this issue.

---

### Post by TheFu on 2024-09-08
I didn't look at the images. I don't trust that image site. Sorry.

The easiest answer is backup any data/settings you don't want to lose, then to do a fresh install.  Getting good at that process will help you for decades on any OS.  

With Ubuntu/debian (and most Linuxen), the backups are really easy.  A fresh install of the OS is really easy.  Bringing back your files from $HOME is easy.  Reloading all the programs you've installed is a little harder, but not once you know the CLI commands to accomplish it, then it is really easy.  Once you get each of these things down (know them well), you'll be able to have a fully restored system in 20-45 minutes.  The restore time depends on 
[LIST]
[*]your internet connection, 
[*]already having an install ISO on a flash drive (which is a good idea anyway for some issues can only be solved with that)
[*]the total amount of data to be restored and 
[*]how many customized settings are NOT stored under your HOME directory.
[/LIST]
I bet you've spent more time than that already.

Of course, it could be sometime as simple as the nouveau drivers being blacklisted. I don't have any nvidia GPUs anymore, so I never have this sort of issue anymore.  [https://askubuntu.com/questions/841876/how-to-disable-nouveau-kernel-driver](https://askubuntu.com/questions/841876/how-to-disable-nouveau-kernel-driver) is how to disable nouveau. You want to enable them.  The file, /etc/modprobe.d/blacklist-nouveau.conf might be named differently on your system.  Use **sudoedit ** to safely edit system files.  Also, making a .bak copy of the file before editing would be smart.  This is just a guess. Maybe 10% likely to help.

---

### Post by grahammechanical on 2024-09-08
Just to be clear. You are able to get to a working desktop using Ubuntu Advanced Options and selecting a Linux kernel with recovery mode. Yes? You then select Resume. Yes? That usually means that Ubuntu is loading using a open source video driver - Nouveau for those of us with Nvidia graphic cards.

Now load Software and Updates>Additional Drivers tab. Allow time for the utility to search the internet for Nvidia proprietary drivers. Then disable whatever option is ticked and select an alternative video driver. Or, disable the proprietary video drivers and continue using the open source video driver if that seems adequate.

The Software and Updates>Additional Drivers tab does the work for us. 

Regards

---

