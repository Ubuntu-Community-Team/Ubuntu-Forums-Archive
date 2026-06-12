---
title: "Cannot login- New issues"
date: 2013-05-05
forum: General Help
---

### Post by RomPirate on 2013-05-05
Hello all

I recently had some problems logging into Ubuntu 12.04. Short list of events:
[LIST=1]
[*]One night I guess I forgot to turn off my laptop, and the battery died- Needed to be plugged into be used (as expected) 
[*]When I tried to log into gnome-session-fallback, it would appear to briefly log in, then take me back to the login screen. I tried this with the unity desktop, as well as the previously installed xmonad wm and still did not work 
[*]I CAN log in TTY1. I found a thread that a had as similar problem with logging in, and suggested changing the owner of ~/.Xauthority using: ```
chown username:username .Xauthority
``` This worked and allowed me to login. 
[*]I noticed my configuration settings were off (Such as animations being re-enabled and the workspace icon being a 2x2 layout vs a horizontal layout). Thinking it was an update issue, I try: ```
sudo apt-get update
``` which gives: ```
sudo: apt-get: command not found
``` 
[*]Googling suggests checking /usr/bin for apt-get which is not there. 
[*]While opening Synaptic Package Manager, I get a popup that states: ```
W: Unable to read /etc/apt/preferences.d/ - DirectoryExists (2: No such file or directory)
``` 
[/LIST]


So what happened to my system, and how can I get it back to the way it was before? Oh how I miss it :(

Thank you all :)



SOLVED:

I used my live Ubuntu 12.04 USB and copied the /etc/apt/preferences.d/ folder to the non working directory for Ubuntu. I of course changed the owner of the folder using: ```
sudo chown username:username preferences.d 
```

I tried to install "apt" through the synaptics package manager, but still got an error about /usr/lib/apt/methods/http missing. I did the same thing, copied the file from the live USB and put it in the right directory. apt is now installed in synaptics package manager, and I can update Ubuntu again. My settings are still off so I'll have to play around with it again to get everything in order.

---

### Post by dino99 on 2013-05-05
boot in recovery mode (hit "shift" key down at bios end process to get the grub menu with a single os installation), activate the network, and select "dpkg" to fix the system, finally select to "continue"

---

### Post by RomPirate on 2013-05-05
> **dino99 said:**
> boot in recovery mode (hit "shift" key down at bios end process to get the grub menu with a single os installation), activate the network, and select "dpkg" to fix the system, finally select to "continue"

Wow, Thank you for the quick response! 

Unfortunately when I try "dpkg" i get a few errors:

```
rm: cannot remove '/var/lib/apt/lists/partial/*': No such file or directory
rm: cannot remove '/var/cache/apt/archives/partial/*': no such file or directory
/lib/recovery-mode/options/dpkg: 36: /lib/recovery-mode/options/dpkg: apt-get not found
/lib/recovery-mode/options/dpkg: 37: /lib/recovery-mode/options/dpkg: apt-get not found
/lib/recovery-mode/options/dpkg: 38: /lib/recovery-mode/options/dpkg: apt-get not found
Finished, please press ENTER

```

After this, I continue to boot Ubuntu and login. The resolution is off as expected, but all of the problems still persist :( Rebooting normally also produces the same issues. I've got a live usb at my disposal if it makes any difference.

Thanks!

---

